```
---
- hosts: localhost
  gather_facts: no
  connection: local

  vars:
    aws_region: us-east-1
    aws_profile: default
    s3_bucket_name: jenkins-backup
    jenkins_home: /var/lib/jenkins

  tasks:
    - name: Ensure an S3 bucket exists for the backups.
      s3_bucket:
        name: "{{ s3_bucket_name }}"
        versioning: yes

    - name: Sync the contents of JENKINS_HOME to S3.
      command: >
        aws s3 sync . s3://{{ s3_bucket_name }}
        --delete
        --only-show-errors
        --exclude '.aws/*'
        --exclude '.ssh/*'
        --exclude 'workspace/*'
        --exclude 'workspace'
      args:
        chdir: "{{ jenkins_home }}"
      register: sync_command
      # See: https://github.com/ansible/ansible/issues/32472
      failed_when: False
      # Allow up to 1 hour for this task to complete, check every 20s.
      async: 3600
      poll: 20

    # See: https://github.com/aws/aws-cli/issues/2473
    - name: Confirm sync command completed without any critical failures.
      assert:
        that: sync_command.rc == 0 or sync_command.rc == 2

    - debug:
        msg: "Backup to s3://{{ s3_bucket_name }} complete."
```

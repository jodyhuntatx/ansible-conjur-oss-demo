# Ansible & Conjur OSS Quickstart

1) run start-conjur
2) run setup-ansible-demo.sh
3) use output from setup script to create a Conjur credential retriever
4) verify the credential retriever can retrieve the aws-access-key and aws-secret-key values
5) create an Amazon Web Services credential
6) replace the Access Key value with the Conjur Credential Retriever that retrieves the aws-access-key value
7) replace the Secret Key value with the Conjur Credential Retriever that retrieves the aws-secret-key value
8) create a job template that uses the AWS credential and runs the following playbook:
```
---
- hosts: all
  gather_facts: False
  tasks:
    - debug:
        msg:
        - Access Key is {{ lookup('env', "AWS_ACCESS_KEY_ID") }}
        - Secret Key is {{ lookup('env', "AWS_SECRET_ACCESS_KEY") }}
```
9) run the job and examine the output
10) change the value of one or both variables using the conjur-variable script.
    e.g.:
```
	>> ./conjur-variable set aws-access-key a-new-value
```
11) run the job again and examine the output for the new value.


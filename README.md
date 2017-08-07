# Minimal Ghost Blog in AWS

## AWS Account

An AWS account is required for this playbook to work.

*Note:* It will create resources in us-east-1.  If you have resources already running in this region please change the region used or verify it will not interfere with your setup.

*Note:* These AWS resources will cost money, please setup a budget on your AWS account so your spending does not go higher than expected.  Also tear down any resources you will not use.

## AWS Credentials

This Playbook relies on the boto.config to have AWS_SECRET_KEY and AWS_ACCESS_KEY vars to be present. These vars should be set to your accounts AWS Secrety Key and Access Key that have sufficient privileges to create a VPC, IGW, Route Table and EC2 instance.  A sample IAM role for such a user is provided in this repo.

## ghost-blog.pem

A pem file will be needed in order to create an ec2 instance and to log into it to configure it.  Please create this pem file in the region the instance will be created and name it `ghost-blog.pem`. The region used by this playbook is `us-east-1`

## Ansible Setup

There are a few ways to run Ansible but the easiest is just to install it locally.

Installation: [Ansible install](http://docs.ansible.com/ansible/latest/intro_installation.html)

Other options are to run Vagrant box or Docker image with Ansible installed.  The upside of these options are that the environment is always the same and you don't have to worry about any updates to python that may affect yoru installed version of Ansible.

This playbook also requires Boto.  To install run the following command:
```
pip install boto
```

## Running the Playbook

First update `group_vars/all/ghost.yml` with your blog's information then run the following commands.


```
ssh-add ghost-blog.pem
BOTO_CONFIG=$(pwd)/boto.config ansible-playbook playbooks/setup_ghost.yml

```

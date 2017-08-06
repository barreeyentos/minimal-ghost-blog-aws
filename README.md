# Minimal Ghost Blog in AWS

## AWS Credentials

This Playbook relies on an aws.cfg file to be present. In that file you need to insert your accounts AWS Secrety Key and Access Key that has sufficient privileges to create a VPC, IGW, Route Table and EC2 instance.  A sample IAM role for such a user is provided in this repo.

## Ansible Setup

There are a few ways to run Ansible but the easiest is just to install it locally.

Installation: [Ansible install](http://docs.ansible.com/ansible/latest/intro_installation.html)

Other options are to run Vagrant box or Docker image with Ansible installed.  The upside of these options are that the environment is always the same and you don't have to worry about any updates to python that may affect yoru installed version of Ansible.

## Running the Playbook

First update `group_vars/all/ghost.yml` with your own information then run the following command.

```
ansible-playbook playbooks/setup_ghost_blog.yml
```

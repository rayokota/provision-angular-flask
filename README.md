# The Angular-Flask provisioner 

An [Ansible](http://www.ansible.com/home) provisioner for [AngularJS](http://angularjs.org)  and [Flask](http://flask.pocoo.org).

This provisioner installs the [Angular-Flask generator](https://github.com/rayokota/generator-angular-flask) and all prerequisites.  Currently it only supports Ubuntu 12.04.

## Installation

Install [Ansible](http://www.ansible.com/home) and [Vagrant](http://www.vagrantup.com).

## Usage with AWS

Obtain an [AWS](http://aws.amazon.com) account.  

Set up AWS environment variables as follows:

    export AWS_ACCESS_KEY_ID="XXXXXXXXXXXXXXXXXXXX"    
	export AWS_SECRET_ACCESS_KEY="XXXXXXXXXXXXXXXXXXXX"
	export AWS_KEYPAIR_NAME="my-keypair-name"
	export AWS_SSH_PRIVATE_KEY_PATH="/path/to/my-keypair.pem"

Run Vagrant:

    vagrant up --provider=aws

Connect to the VM:

    vagrant ssh
    
Destroy the VM when done:

    vagrant destroy

## Usage with VirtualBox

Install [VirtualBox](https://www.virtualbox.org).

Run Vagrant:

    vagrant up --provider=virtualbox

Connect to the VM:

    vagrant ssh
    
Destroy the VM when done:

    vagrant destroy


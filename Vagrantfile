# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # For information on available options for Ansible provisioning, please visit:
  # http://docs.vagrantup.com/v2/provisioning/ansible.html
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "setup.yml"
    #ansible.inventory_path = "ansible_hosts"
    ansible.verbose = "vvv"
    ansible.extra_vars = "ansible_extra_vars.yml" if File.exist? "ansible_extra_vars.yml"
  end

  # For information on available options for the Virtualbox provider, please visit:
  # http://docs.vagrantup.com/v2/virtualbox/configuration.html
  config.vm.provider :virtualbox do |vb, override|
    override.ssh.username = "vagrant"
    override.vm.box = "precise64"
    override.vm.box_url = "http://files.vagrantup.com/precise64.box"
    override.vm.network :forwarded_port, guest: 3000, host: 3000
    override.vm.network :forwarded_port, guest: 5000, host: 5000
    override.vm.network :forwarded_port, guest: 8080, host: 8080
    override.vm.network :forwarded_port, guest: 9000, host: 9000
    override.vm.network :forwarded_port, guest: 9292, host: 9292
    #override.vm.network :private_network, ip: "192.168.222.111"
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # This configuration is for our EC2 instance
  config.vm.provider :aws do |aws, override|
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    # ubuntu AMI
    aws.ami = "ami-59a4a230"
    aws.instance_type = "t1.micro"
    aws.keypair_name = ENV['AWS_KEYPAIR_NAME']
    aws.security_groups = ["default"]
    aws.tags = {
      'Name' => 'angular-flask'
    }

    override.vm.box = "dummy"
    override.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"
    override.ssh.username = "ubuntu"
    override.ssh.private_key_path = ENV['AWS_SSH_PRIVATE_KEY_PATH']
  end
end

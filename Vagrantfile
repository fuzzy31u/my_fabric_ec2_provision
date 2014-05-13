# -*- mode: ruby -*-
# vi: set ft=ruby :

# see http://d.hatena.ne.jp/fuzzy31u/20140508/1399558256

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "aws"

  config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__auto: "true"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id     = "<ACCESS_KEY_ID>"
    aws.secret_access_key = "<SECRET_ACCESS_KEY>"
    aws.keypair_name = "<KEYPAIR_NAME>"
    aws.instance_type = "t1.micro"
    aws.region = "ap-northeast-1"
    aws.ami = "ami-c9562fc8"
    aws.security_groups = [ '<SECURITY_GROUPS>' ] 

    override.ssh.username = "<SSH_USERNAME>"
    override.ssh.private_key_path = "<SSH_PRIVATE_KEY_PATH>"

    config.vm.provision :fabric do |fabric|
      fabric.fabfile_path = "./provision.py"
      fabric.tasks = ["<TASKS>"]
    end

  end

end
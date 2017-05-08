# Vagrant

```
>> vagrant init     # to generate `Vagrantfile`
>> vagrant up       # to provision a VM with Vagrantfile
>> vagrant ssh      # to connect the provisioned VM via SSH
>> vagrant destroy  # to destroy the provisioned VM
```

# Trouble Shooting
## Fail to connect the Internet
* When I used `ping google.com`, I received the `unknown host: google.com` error.
* How to fix:
    * Add the following code to `Vagrantfile`
```
config.vm.provider "virtualbox" do |v| 
  v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
end
```

* [Ref] https://askubuntu.com/questions/238040/how-do-i-fix-name-service-for-vagrant-client


## my vagrant's files:

#### The bastion Host vagrantFile

###### On the vagrant host execute:

```
mv BastionHost-Vagrantfile Vagrantfile
vagrant plugin install vagrant-vbguest 
vagrant up
```

Obs.: The plugin vagrant-vbguest is necessary to share folders with the host:

https://github.com/dotless-de/vagrant-vbguest

#### The bastion Host Vagrantfile

###### Dependencias

[VirtualBox (Provider)](https://www.virtualbox.org/wiki/Downloads)

[Vagrant](https://www.vagrantup.com/downloads.html)


###### On the vagrant host execute:

```
vagrant plugin install vagrant-vbguest 
vagrant up
```

Obs.: The plugin [vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest) is necessary to share folders with the host.

#### Distro: Centos 7

|Packages       |
| -----------   |
| awscli        |
| vim			|
| putty         |
| git           |


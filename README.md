# animation-vm
This repo provides an [ubuntu][ubuntu] Virtual Machine preconfigured with tools for animation creation

### Screenshot

![alt text](https://github.com/thomasliebig/animation-vm/screenshots/screenshot1.png "Screenshot")

### Installation

Install [virtualbox][virtualbox] and [vagrant][vagrant] then git clone this repository and bring the machine initially up with

```sh
 vagrant up
``` 

The files in this repo are mounted into the VM  at /vagrant

Stop machine with

```sh
 vagrant halt
``` 
 and resume with 
```sh
 vagrant reload
``` 
### Login Credentials
```sh
user: vagrant
pass: vagrant
```

### Usage
start virtual machine as stated above and use the virtualbox user interface. Login with the given credentials and start graphical system by typing:
```sh
startx
```


> [Thomas Liebig][tliebig] <thomas@thomas-liebig.eu>

   [ubuntu]: <http://www.ubuntu.com/>
   [virtualbox]: <https://www.virtualbox.org/>
   [vagrant]: <https://www.vagrantup.com/>
   [tliebig]: <http://www.thomas-liebig.eu>

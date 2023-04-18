# VM-Dev-environments

# What is a Virtual machine?

A A virtual machine is a software-based emulation of a physical computer system. It enables one or multiple operating systems to run simultaneously on a single physical machine. Each virtual "guest" machine runs it's own operating system and functions seperately from the other virtual machines. This is the case even if they are all running on the same host.

# What is a Dev environement?

![image](https://user-images.githubusercontent.com/129381619/232557781-bb3344d3-ff0e-425c-a357-b304aa961bec.png)


A developement environement is a set up of software tools and configurations that are used by Developers to create and test software. The environment allows develops to experiment without worrying about effect it'll have with the experience of real users.

# What is the purpose of a dev environment?

The purpose of creating a dev environment is to provide a safe and isolated environment for developers to write and test their code without affecting the production environment. By using a dev environment, developers can ensure that their code is working correctly before deploying it to production, which can help to prevent bugs and errors from impacting end-users. The dev environment typically includes tools such as a code editor, a debugger, and a version control system.

# What is a vagrant?

![image](https://user-images.githubusercontent.com/129381619/232559772-4ba5c83a-8b3e-424c-9811-3c51aaf099d6.png)

Vagrant is an open-source tool for building and managing virtual machine environments. It allows developers to easily create, configure, and share portable development environments that can be used across different operating systems and platforms.

# Vagrant virtualbox connection

1) After ensuring you have installed both Vagrant and VirtualBox, create a new directory for a Vagrant project. You can do this by using the gitbash command ```mdkir 'filename'```. 

2) Now open the Git Bash terminal and initialise the new vagrant project using ```vagrant init```. Make sure you're in the created directory before initialising.

3) Go on VirtualStudio code and and open the vagrant file and change the ```config.vm.box``` line to ```config.vm.box = "ubuntu/xenial64"```. This will ensure that we have Ubuntu on our VM.

It should like below:

```
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
end
```

4) Now type ```vagrant up``` in the terminal and this should send a command to start the VM

5) Now we can use ```vagrant ssh`` to ssh into the vm and another terminal session will open up in the vm


# What makes a good dev environment?


# 4 pillars of DevOps?



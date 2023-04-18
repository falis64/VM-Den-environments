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

6) Download the app and environment zip file and make sure to unzip it (you can do this double clicking on the right and selecting extract all)

7) Now make sure to put in the Virtualisation folder and check on VSCode to see that it's there

8) Now sync the app by using the command ```config.vm.synced_folder "app", "/home/vagrant/app"```

9) To check that you have nginx installed, type ```http://192.168.20.100/``` into the browser and you should get this

<img width="413" alt="image" src="https://user-images.githubusercontent.com/129381619/232787983-94df1a0f-b02e-4124-b675-bba52b9a2c6c.png">

10) Now to install nodejs version 6.x, first use the command ```sudo apt-get install python-software-properties```

11) Then use the command ```curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -```

12) Finally use the command ```sudo apt-get install nodejs -y```

13) You can check that you have the correct version of nodejs by using the command ```nodejs --version```. You shoould see something like this:

<img width="233" alt="image" src="https://user-images.githubusercontent.com/129381619/232789921-5530802e-1d3d-4063-b723-cc680e92fa4c.png">

14) Now to install pm2, use the commmand ```sudo npm install pm2 -g```

15) Make sure you're in the app folder, you can do this by checking ```pwd``` or go into the file by ```cd```

16) Once you're in the app, use the code ```node app.js``` 

17) You should now see this:
<img width="251" alt="image" src="https://user-images.githubusercontent.com/129381619/232795576-4865ab38-773d-4fa6-88a8-f404657fa519.png">

18) You're now ready to go into your app, simply type ```http://192.168.20.100:3000/``` into the browser and you should see this:

<img width="395" alt="image" src="https://user-images.githubusercontent.com/129381619/232796117-13c107aa-a043-4b7f-a072-73191740c697.png">


# What makes a good dev environment?


# 4 pillars of DevOps?



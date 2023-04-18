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

4) Now type ```vagrant up``` in the VSCode terminal and this should send a command to start the VM in the virtual box

5) Now we can use ```vagrant ssh`` to access the vm and another terminal session will open up in the vm

6) You can update and upgrade your vm using the following commands in the Git Bash app:

```
#!/bin/bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install nginx -y
sudo systemctl restart nginx
sudo systemctl enable nginx
```

7) In order to access the ip address for your vm, you need to update the vagrant file. As you can see below, we have used a private ip address and now type ```vagrant reload``` in the vscode and ```vagrant ssh``` in the Git Bash.

```Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network" ip: "192.168.10.100"

end
```
8) You can check if the ip address is working properly by typing it into your web browser. If it is working then you should see a message welcoming you to Nginx.

# Installing an app on Virtual Machine using Vagrant

The content of your vagrant should be:

```
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip: "192.168.20.100"

  # provision in the vm
  config.vm.provision "shell", path: "provision.sh"

  # syncing the app folder
  config.vm.synced_folder "app", "/home/vagrant/app"

end
```
9) Now we can run a test to check our environment is correct by using the commands below:
```gem install bundler`` this will allow us to bundle all tests together
```bundle``` this bundles all the tests
```rake spec``` this command will run the tests. It was created by the developers.

10) If the test is successful, it'll show what we're missing. Now follow the steps below

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

# Automating all dependencies

In order to automate all the dependencies, follow the steps below:

1) Go on VSCode provision file and type this codes below:
```
sudo apt-get install python-software-properties
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install nodejs -y
sudo npm install pm2 -g
cd /home/vagrant/app
sudo npm install
```
2) Now on your VSCode terminal, run the command ```vagrant up```

3) Once it's finished running, go on Git Bash and run the command ```vagrant ssh``` - you'll get something like:

<img width="372" alt="image" src="https://user-images.githubusercontent.com/129381619/232809823-6ec1a592-c76e-4e32-aa3c-59feab51a3f8.png">

4) Once you have done this, ```cd``` into the directory where the app is, like below:

<img width="203" alt="image" src="https://user-images.githubusercontent.com/129381619/232810037-7d054cb0-7177-4723-aeb6-ee2bec034c1a.png">

5) Once you're in the app, run the command ```node app.js```. If it's successful, you'll see the message below:

<img width="248" alt="image" src="https://user-images.githubusercontent.com/129381619/232810485-4d1002f6-6417-4a9e-bb7b-a0c28ad5ea13.png">

You can now type ```http://192.168.20.100:3000/``` into the browser and if it's success you'll see a message welcoming you into the Sparta app.


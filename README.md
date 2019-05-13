# vagrant-virtual-enviroment

This repository contains a folder with contents which can be used to set up a development environment using the software tools vagrant and virtual box.


Download and install vagrant:
https://www.vagrantup.com/downloads.html

Download and install virtual box:
https://www.virtualbox.org/wiki/Downloads



Setting up a vagrant virtual environment:

1) Open your systems terminal.

2) Navigate to the "DevEnviroments" folder using the terminals cd command.

3) Next, enter the following command in the terminal: 
		
			vagrant up

This runs the vagrant file and sets up virtual machine/development environment and installs essential files stated in the provision file.

4) Use the following command to ensure you have the latest vagrant host updater plugin:
		
		vagrant plugin install vagrant-hostsupdater 

5) Next, use the command:
			
			vagrant ssh

This connects the vagrant virtual machine via ssh.

6) Navigate to the apps folder through the vagrant ssh:

			install npm

7) Then enter:

			npm start

8) Finally, enter the command:

			pm2 start app.js
			
This will allow you to directly run an application on the development.localhost:3000 server.




---Explanation of some of the contents of the folder:
1) The folder contains a file called "VagrantFile".
The file contains the following code:

config.vm.box = "ubuntu/xenial64"
-This initialises a vagrant virtual box.

 
config.vm.network("private_network", ip: "192.168.10.100")
config.hostsupdater.aliases = ["development.local"]
-This sets up a private local server for development use. 

config.vm.synced_folder("app", "/app")
-This syncs the applications folder that is in development.


2) An environment folder with a file named provision.sh which contains
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install nodejs -y
sudo npm install -g pm2
node app.js
pm2 start app.js

--This code will install various tools which facilitates the development environment.

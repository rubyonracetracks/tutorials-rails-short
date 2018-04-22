# Adopt-A-Tree Tutorial

Welcome to the Adopt-A-Tree Tutorial of [Ruby on Racetracks](http://www.rubyonracetracks.com/)!

## Prerequisites
* You should have version 4 of SparkyLinux installed as your host OS or virtual OS. You may also use any other Linux distro based on Debian Stretch.  If you are using a Mac or Windows, you can use a VirtualBox virtual machine with SparkyLinux on it. For more details, go through the [VirtualBox Tutorial](https://github.com/rubyonracetracks/tutorial-virtualbox).
* You should have Docker installed in your SparkyLinux desktop Linux setup.  This is covered in chapter 1 of the [Docker Tutorial](https://github.com/rubyonracetracks/tutorial-docker-stretch).
* You should be familiar with the Ruby on Racetracks way of using Docker for Ruby on Rails.  This is covered in the [Docker Tutorial](https://github.com/jhsu802701/tutorial-docker-stretch).

## Entering the Custom Docker Container
* Enter the following commands in a terminal in SparkyLinux:
```
cd
mkdir OpenTwinCities
cd OpenTwinCities
git clone https://github.com/OpenTwinCities/docker-debian-stretch.git
cd docker-debian-stretch
```
* Create the files for using a Docker container based on the rails-adoptatree Docker image.
  * If you are using 64-bit Linux, enter the following command:
  ```
  sh rails-adoptatree.sh
  ```
  * If you are using 32-bit Linux, enter the following command:
  ```
  sh 32rails-adoptatree.sh
  ```
* Enter the following command to enter the directory for using the development image:
```
cd rails-adoptatree
```
* You will be asked about your desired offset for the port numbers. Enter "1".
* Download the rails-adoptatree Docker image and start a Docker container based on it by entering the following command:
```
sh download_new_image.sh
```
* In a few minutes, you will be automatically logged into the Docker container based on this Docker image.

## Setting Up the App
* In the rails-adoptatree Docker container, enter the command "tmux" to start a tmux window.
* Enter the following commands:
```
git clone https://github.com/OpenTwinCities/adopt-a-tree.git
cd adopt-a-tree
sh build_fast.sh; sh server.sh
```
* The build_fast.sh script installs the gems, configures the PostgreSQL database, and runs the tests. This process takes just a few minutes. If all goes well, all of the tests will pass.

## Viewing the App
* Once the server is running, go to the URL http://localhost:3001/ in your web browser in SparkyLinux to view the Adopt-A-Tree app.
* NOTE: The ports.txt file in the shared directory shows which ports in desktop Linux correspond to the critical ports in the app in Docker.  Port 3000 in Docker equates to port 3001 in the desktop Linux system.

## Viewing the App's Database
* Open pgAdmin in SparkyLinux to view the data in the Adopt-A-Tree app.
* In the upper left corner of the pgAdmin window, click on the plug icon to add a server.
* Fill in the following server parameters:
  * Name: adopt-a-tree
  * Host: localhost
  * Port: 15433
  * Username: adopta
  * Password: password1
* NOTE: The ports.txt file in the shared directory shows which ports in the host correspond to the critical ports in the app in Docker.  Port 5432 in Docker equates to port 15433 in the desktop Linux system.
* In the Object browser, go to Server Groups -> Servers -> adopt-a-tree -> Databases -> adopta_development -> schemas -> public - Tables.  Right-click on the desired object and go to View Data -> View All Rows.  You can now see the data.

## Entering Commands
* In the DOcker container, press Ctrl-b and then "c" to create a new tmux window.
* Enter the command "cd adopt-a-tree".
* Use this new tmux window (Window 1) for entering commands.  The original tmux window (Window 0) is dedicated to the Rails server.

## Mail Server
* In the Docker container, enter the command "sh mailcatcher.sh".  This runs the mail server.
* Go to the URL http://localhost:1081/ in your web browser in SparkyLinux to view the development environment emails.  This email interface simulates the user experience.
* NOTE: The ports.txt file in the shared directory shows which ports in the host correspond to the critical ports in the app in Docker.  Port 1080 in Docker equates to port 1081 in the desktop Linux system.

# Short Ruby.MN Tutorial

Welcome to the Short Ruby.MN Tutorial of [Ruby on Racetracks](http://www.rubyonracetracks.com/)!  Please note that this tutorial sets up the existing Ruby.MN project.  The Long Ruby.MN Tutorial that walks you through the process of replicating the new Ruby.MN app is at [https://github.com/jhsu802701/tutorial-rails-rubymn2](https://github.com/jhsu802701/tutorial-rails-rubymn2).

## Prerequisites
* You should have version 4 of SparkyLinux installed as your host OS or virtual OS. You may also use any other Linux distro based on Debian Stretch.  If you are using a Mac or Windows, you can use a VirtualBox virtual machine with SparkyLinux on it. For more details, go through the [VirtualBox Tutorial](https://github.com/jhsu802701/tutorial-virtualbox).
* You should have Docker installed in your SparkyLinux desktop Linux setup.  This is covered in chapter 1 of the [Docker tutorial](https://github.com/jhsu802701/tutorial-docker-stretch).
* You should be familiar with the Docker way of developing in Ruby on Rails.  This is covered in the [Docker tutorial](https://github.com/jhsu802701/tutorial-docker-stretch).

## Entering the Custom Docker Container
* Enter the following commands in a terminal in SparkyLinux:
```
cd
mkdir jhsu802701
cd jhsu802701
git clone https://github.com/jhsu802701/docker-debian-stretch.git
cd docker-debian-stretch
```
* Create the files for using a Docker container based on the rails-rubymn2 Docker image.
  * If you are using 64-bit Linux, enter the following command:
  ```
  sh rails-rubymn2.sh
  ```
  * If you are using 32-bit Linux, enter the following command:
  ```
  sh 32rails-rubymn2.sh
  ```
* Enter the following command to enter the directory for using the development image:
```
cd rails-rubymn2
```
* You will be asked about your desired offset for the port numbers. Enter "3".
* Download the rails-rubymn2 Docker image and start a Docker container based on it by entering the following command:
```
sh download_new_image.sh
```
* In a few minutes, you will be automatically logged into the Docker container based on this Docker image.

## Setting Up the App
* In the rails-adoptatree Docker container, enter the command "tmux" to start a tmux window.
* Enter the following commands:
```
git clone https://github.com/jhsu802701/rubymn2.git
cd rubymn2
sh build_fast.sh; sh server.sh
```
* When you are prompted for the username and password, just press Enter to use the default values.  
* The build_fast.sh script installs the gems, configures the PostgreSQL database, and runs the tests. This process takes just a few minutes. If all goes well, all of the tests will pass.
* Note that your database username and password are now stored in the config/application.yml file in your app.

## Viewing the App
* Once the server is running, go to the URL http://localhost:3003/ in your web browser in SparkyLinux to view the Ruby.MN app.
* NOTE: The ports.txt file in the shared directory shows which ports in desktop Linux correspond to the critical ports in the app in Docker.  Port 3000 in Docker equates to port 3003 in the desktop Linux system.

## Viewing the App's Database
* Open pgAdmin in SparkyLinux to view the data in the new Ruby.MN app.
* In the upper left corner of the pgAdmin window, click on the plug icon to add a server.
* Fill in the following server parameters:
  * Name: rubymn2
  * Host: localhost
  * Port: 15435
  * Username: username_db_rubymn2
  * Password: long_way_stinks
* NOTE 1: The config/application.yml file contains the username and password.
* NOTE 2: The ports.txt file in the shared directory shows which ports in the host correspond to the critical ports in the app in Docker.  Port 5432 in Docker equates to port 15435 in the desktop Linux system.
* In the Object browser, go to Server Groups -> Servers -> rubymn2 -> Databases -> db_rubymn2_dev -> schemas -> public - Tables.  Right-click on the desired object and go to View Data -> View All Rows.  You can now see the data.

## Entering Commands
* In the Docker container, press Ctrl-b and then "c" to create a new tmux window.
* Enter the command "cd rubymn2".
* Use this new tmux window (Window 1) for entering commands.  The original tmux window (Window 0) is dedicated to the Rails server.

## Mail Server
* In Window 1 of the Docker container, enter the command "sh mailcatcher.sh".  This runs the mail server.
* Go to the URL http://localhost:1081/ in your web browser in SparkyLinux to view the development environment emails.  This email interface simulates the user experience.
* NOTE: The ports.txt file in the shared directory shows which ports in the host correspond to the critical ports in the app in Docker.  Port 1080 in Docker equates to port 1081 in the desktop Linux system.
* In the local browser window at http://localhost:3003/, sign up for an account.  A new email message will appear at http://localhost:1081/.  You can click on the link in the message to confirm your registration.

## Testing the Code
* In Window 1 of the Docker container, enter the command "sh test_code.sh", which is executed in the build_fast.sh script.  This test_code.sh script runs the brakeman, sandi_meter, bundle-audit, rubocop, rails_best_practices, and gemsurance analysis tools.
* Note that the above tools may flag parts of your code even if all of the build tests pass.  The issues flagged by these tools won't stop your app from working but will point to security vulnerabilities and code that is not optimally written.
* The brakeman and bundle-audit tools will warn you of security vulnerabilities.  The sandi_meter, rubocop, and rails_best_practices tools warn of lower quality code.  The gemsurance tool warns you of outdated gems and gems with security vulnerabilities.  Its results are printed at log/gemsurance_report.html.

## Outlining the Code
* In Window 1 of the Docker container, enter the command "outline.sh", which is executed in the build_fast.sh script.
* This outline.sh script runs the annotate tool (which adds comments listing object parameters to key files), generates outlines of the app in the notes directory, and generates block diagrams of your app in the log directory.

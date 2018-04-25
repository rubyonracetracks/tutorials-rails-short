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
* Create the files for using a Docker container based on the rbenv-rubymn2 Docker image.
  * If you are using 64-bit Linux, enter the following command:
  ```
  sh rbenv-rubymn2.sh
  ```
  * If you are using 32-bit Linux, enter the following command:
  ```
  sh 32rbenv-rubymn2.sh
  ```
* Enter the following command to enter the directory for using the development image:
```
cd rbenv-rubymn2
```
* You will be asked about your desired offset for the port numbers. Enter "3".
* Download the rbenv-rubymn2 Docker image and start a Docker container based on it by entering the following command:
```
sh download_new_image.sh
```
* In a few minutes, you will be automatically logged into the Docker container based on this Docker image.

# Generic App Tutorial

This [Ruby on Racetracks](http://www.rubyonracetracks.com/) tutorial provides an introduction to my [Generic App](https://github.com/rubyonracetracks/generic_app) gem, which allows you to start a new app based on an existing Rails template.  In just seconds, you can have a high quality app with comprehensive tests, static pages, user authentication, and admin authentication already provided.

## Prerequisites
* Docker should be installed.  This is covered in the [Docker Tutorial](https://github.com/rubyonracetracks/tutorial-docker-stretch).
* You should have one of my rails-general Docker images installed.  This is covered in the [Docker Tutorial](https://github.com/rubyonracetracks/tutorial-docker-stretch).
* You should be familiar with the process of creating a new Rails app.

## Getting Started
* Use the reset.sh script to enter a Docker container based on one of my rails-general Docker images.
* Enter the command "gem install generic_app".
* Enter the following commands:
```
DATE=`date +%Y%m%d-%H%M%S-%3N`
APP_NAME=sample-$DATE
echo $APP_NAME # The name of your app
```
* Enter the command "generic_app".
* When prompted for the directory name of your new app, use the value of $APP_NAME that you printed out.
* When prompted, enter your email address.
* When prompted for the name of your new app, enter "My Sample Rails App".
* In a few seconds, your new app will be ready.
* Go to the README-to_do.txt file for further instructions.

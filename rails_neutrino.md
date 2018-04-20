# Rails Neutrino Tutorial

This [Ruby on Racetracks](http://www.rubyonracetracks.com/) tutorial provides an introduction to my [Rails Neutrino](https://github.com/rubyonracetracks/rails_neutrino_5) scripts, which AUTOMATICALLY generate a Ruby on Rails app from scratch.  This is the tool used to generate the Rails template app used by my [Generic App](https://github.com/rubyonracetracks/generic_app) gem.

## Prerequisites
* Docker should be installed.  This is covered in the [Docker Tutorial](https://github.com/rubyonracetracks/tutorial-docker-stretch).
* You should have one of my rails-general Docker images installed.  This is covered in the [Docker Tutorial](https://github.com/rubyonracetracks/tutorial-docker-stretch).
* You should be familiar with the process of creating a new Rails app.

## Getting Started
* Use the reset.sh script to enter a Docker container based on one of my rails-general Docker images.
* Enter the following commands:
```
git clone https://github.com/rubyonracetracks/rails_neutrino_5.git
cd rails_neutrino_5
sh main.sh
```
* The process of generating a new Rails app will begin.  The app generating process takes several minutes, but it provides a high quality app in the end in FAR less time and with FAR less effort than it would take to do so manually.
* Go to the README-to_do.txt file for further instructions.  You can skip the parts about updating the GenericApp gem.

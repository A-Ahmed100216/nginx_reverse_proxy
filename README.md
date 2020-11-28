# Nginx Reverse Proxy


## Introduction

Our app is currently running on port 3000, in our multi vagrant machine.
This fine for development but browsers use port 80 by default to load web applications.

We could get the app to run on port 80 but that requires giving the app more privileges than we want to which is very dangerous.

We need to set up a reverse proxy.

## Pre-Requisites
* Vagrant
* Virtual Box
* Git

## Tasks

Research how to install and configure Nginx as a reverse proxy. This will listen for requests on port 80 and pass them on to our app on port 3000.

## Acceptance Criteria

* Uses vagrant file
* Localhost set to development.local (unless you computer can't handle this)
* Port 80 has App running (you see the Sparta logo on development.local)
* Work with only command "vagrant up" &/or minimum commands
* Documentation exists as README.md file and includes
introduction, pre-requisites  and instructions.
* Instructions have a clear step by step.
* Repo exists on GitHub.

## Instructions
1. Run `vagrant up app` and `vagrant up db`
2. Navigate to the following webpage which should display the Sparta logo.    
http://development.local
3. Check the fibonacci generator at http://development.local/fibonacci/3
4. The posts page will need some added commands:
```bash
# Login to vagrant
vagrant ssh
# Create an environment variable for DB_HOST
echo "DB_HOST='192.168.10.2'" >> ~/.bashrc
# Reload the bash terminal
bash
# Navigate to app location
cd /home/ubuntu/app/
# Stop the app
pm2 stop app.js
# Export DB_HOST
export DB_HOST
# Start the app again
pm2 start app.js --update-env
```

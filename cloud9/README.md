# Cloud9 instance

A Cloud9 instance with latest version from https://github.com/c9/core

The goal is to provide the lightest possible image. 

Latest is build on node:slim. 
Other tags exist ready for some programming language ([alpine](https://github.com/sapk/dockerfiles/blob/master/cloud9/Dockerfile.alpine), [golang](https://github.com/sapk/dockerfiles/blob/master/cloud9/Dockerfile.golang), [golang-alpine](https://github.com/sapk/dockerfiles/blob/master/cloud9/Dockerfile.golang.alpine), [cordova-android](https://github.com/sapk/dockerfiles/blob/master/cloud9/Dockerfile.cordova-android)).

Docker hub: https://registry.hub.docker.com/u/sapk/cloud9/

## Usage

### Start with auth

    docker run -d -v $(pwd):/workspace -p 8181:8181 sapk/cloud9 --auth username:password
    
You can also use any starting option describe in : https://github.com/c9/core

### Use custom user settings

    docker run -d -v $(pwd):/workspace -v /home/user/c9.settings:/root/.c9/user.settings -p 8181:8181 sapk/cloud9

Where /home/user/c9.settings is the user.settings file on your file system

## Notes

If you want to only expose cloud9 localy use -p 127.0.0.1:8181:8181 instead of -p 8181:8181. Otherwise it will be accesible to any equipement that can acces to your PC through the network.

You need to set auth because if not set the server will only listen to inner-container localhost host and wouldn't be available to the host.

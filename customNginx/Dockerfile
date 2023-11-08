#####################
# Simple nginx image
#####################
FROM ubuntu:bionic

# add an environment varialbe
ENV NGINX_VERSION 1.14.0-0ubuntu1.11

#every time we build the image it only rebuilds the layers that change so
#its best to do apt-get update each time.

RUN apt-get update && apt-get install -y curl
RUN apt-get update && apt-get install -y nginx=$NGINX_VERSION

# Sets the current working directory
# effects the build/decides what directory your in in the container
# The final WORKDIR that appears in docker file decides where CMD and everything 
# is run at the end of the file
#You can use multiple workdirs everything runs in the context of the workdir before it.
#Absolute or relative.
WORKDIR /var/www/html

# move files into the container
# because we just did the /var/www/html thats where we are working!
# Coudl use ADD instead --> also ADD can copy files from a URL
# ADD cana lso extract an archive.
COPY index.html ./

#Documents ports your image is intended to listen on
#it DOESNT publish the port or enable docker to publish it!
EXPOSE 80


#specify command you want to run in the container
#if no custom command run on docker run it will run this command by default
CMD ["nginx", "-g", "daemon off;"]

#nice to put at the end, it effects the container after its already running
#specify which termination signal will be sent to the container process
#in order to terminate it
STOPSIGNAL SIGTERM
#custom health check for docker container to verify its running properly
HEALTHCHECK CMD curl localhost:80
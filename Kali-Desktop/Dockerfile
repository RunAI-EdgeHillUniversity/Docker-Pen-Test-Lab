#Base Image URL
FROM linuxserver/kali-linux:latest
#Install Tools
RUN apt-get update && apt-get full-upgrade -y
RUN apt-get install -y net-tools
RUN apt-get install -y iputils-ping 
RUN apt-get autoremove -y
#Copy files to image
COPY Activities\ /config/Desktop/Activities
#Forewarning: This is just the stuff created by the department's tech team. If you're looking for academic activities for students to carry out, you'll need to forge your own, I'm afraid. 

This lab came about out of necessity because department visitors could not use our existing VM lab via VirtualBox. To that end, we have crafted this lab for anyone to tinker with, based on the brilliant work of the Linux server/Kali-linux image in Docker. 

I've included the docker files for this project as part of this repository, though you can also find the pre-compiled images in our docker hub here: https://hub.docker.com/u/edgehillcompsci 

=-=-=-=-=-=-=-=-=-=-=-=-=
#This has all been built and tested in a Windows 10 Environment
Install Steps: 

1) Load Docker. 
2) Open PowerShell.

3) Create a Docker Network for your Pen-Test Lab.
	i) docker network create pentest

4) Create your attacker machine (Kali-Linux) by running the below command.
	i) docker run --cpus="2" -d --network=pentest -h attacker --name=kali-linux --security-opt seccomp=unconfined -e PGID=1000 -e TZ=Etc/GMT -e SUBFOLDER=/ -e TITLE="Kali Linux " -p 3011:3000 -p 3009:3001 --memory="4gb"  --rm edgehillcompsci/kali-desktop:latest
	ii) Open a web browser (Firefox, Chrome, Edge) and go to: http://localhost:3011/
		> Note: You may need to double-click the desktop to get rid of the select tool or paste option. 

5) Create your victim machine (Metasploitable2)
	i) Open a second PowerShell session and run the below command. 
	ii) docker run --network=pentest -h victim --rm -it --name metasploitable2 edgehillcompsci/metasploitable2
	iii) Metasploitable2 will now open in your current PowerShell window. 

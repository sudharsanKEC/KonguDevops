# Jenkins Installation and Project Deployment Using Docker (Day 3)

This document demonstrates the complete setup of Jenkins on Ubuntu using Docker, configuring Jenkins, cloning a sample project from GitHub, and accessing the project through the Ubuntu VM public IP address.

---

## 1️⃣ Prerequisites

- Ubuntu running inside VMware
- Docker installed and running
- Internet connection
- A public GitHub repository URL (sample project)

---

## 2️⃣ Installing Jenkins Using Docker

Run the following command inside Ubuntu terminal:

```bash
docker run -d \
  -p 8080:8080 \
  -p 50000:50000 \
  --name jenkins \
  jenkins/jenkins:lts
Verify Jenkins container is running:

docker ps
Expected output:

IMAGE                PORTS
jenkins/jenkins:lts  0.0.0.0:8080->8080/tcp
3️⃣ Access Jenkins in Browser
Get Ubuntu IP address:

ip a
Open browser and visit:

http://<ubuntu-ip>:8080
Jenkins unlock screen will appear.

4️⃣ Unlock Jenkins
Retrieve initial admin password:

docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword
Paste the password into browser.

Then:

Select Install Suggested Plugins

Create admin user

Complete Jenkins setup

After completion, Jenkins dashboard will be displayed.

5️⃣ Creating Jenkins Job to Clone GitHub Project
Click New Item

Enter job name: sample-project

Select Freestyle Project

Click OK

Under Source Code Management:

Select Git

Paste GitHub repository URL

Click Save

6️⃣ Build the Project
Click:

Build Now
After build finishes:

Open build number

Click Console Output

You should see:

Cloning repository...
Finished: SUCCESS
This confirms Jenkins successfully cloned the GitHub project.

7️⃣ Verify Cloned Project Inside Jenkins Container
Enter Jenkins container:

docker exec -it jenkins bash
Navigate to Jenkins workspace:

cd /var/jenkins_home/workspace/sample-project
ls
Project files will be visible.

Exit container:

exit
8️⃣ Deploy Cloned Project Using Nginx Container
Start nginx container:

docker run -d -p 8090:80 --name web nginx
Copy cloned project from Jenkins container to nginx:

docker cp jenkins:/var/jenkins_home/workspace/sample-project/. web:/usr/share/nginx/html/
Verify containers:

docker ps
Expected output:

jenkins  0.0.0.0:8080->8080/tcp
web      0.0.0.0:8090->80/tcp
9️⃣ Access Project from Browser
Open browser:

http://<ubuntu-ip>:8090
The cloned GitHub project will now be visible publicly.


# FSND6-Linux-Server-Configuration
Repository for remote  linux server administration


#### To access the server please use the following IP address
34.230.63.255
#### To access the server please use the following SSH port
2200
#### To access the webapp please use the following SSH port
The application is hosted on the following domain:
http://ec2-34-230-63-255.compute-1.amazonaws.com/

#### Summary of software installed and configuration changes
1. Update Ubuntu repository 
sudo apt-get update
2. Upgrade with all new updates
sudo apt-get upgrade
3. Create 2 users (student and grader)
sudo adduser student
sudo  adduser grader
4. Add users to sudoers list
create in /etc/sudoers.d two files (student and grader)
paste with sudo nano grader the following content:
\#User rules for ubuntu
grader ALL=(ALL) NOPASSWD:ALL
5. create SSH ley with Amazon service (or alternatively ssh-keygen)
6. Change SSH port to 2200
sudo nano /etc/ssh/sshd_config
change port line to Port 2200
7. disable remote rooy login
sudo nano /etc/ssh/sshd_config
PermitRootLogin no
AllowUsers grader, student
8. Restart SSH
sudo service ssh restart
9. Create firewall
as per udacity lesson: block all incoming except port 80 and 2200
allow all outgoing and then enable with sudo ufw enable
10. Check that everything works but closing existing connections and restarting woith ssh to port 2200
ssh grader@34.230.63.255 -i ~/Projects/udacity/project_6/keys/grader_ssh.pem -p 2200
11. Install Postgres, PSQL and apache2 with sudo apt-get install
12. Create virtual environment for python
13. Install all required libraries
14. Install and clone repository
15. Configure Postgresql
- go to PSQL with sudo -i -u ppstgres and
- create user catalog. Change user permission with ALTER USER
- create db catalog and change that with ALTER DATABASE catalog OWNER TO catalog;
- . Change PSQL remote connection to allow password login by changing pg_hba.conf file
17. Configure APACHE2 wto run flask with mod_wsgi
https://www.jakowicz.com/flask-apache-wsgi/
18. Change code to run in new environment (a lot of tweaks, including changing FB oauth, excluding some  SQLALCHEMY commands that caused freeze to Postgres)
19.  Run application
Resources used:
Udacity discussions and class notes
https://www.a2hosting.com/kb/getting-started-guide/accessing-your-account/disabling-ssh-logins-for-root
https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2
https://www.jakowicz.com/flask-apache-wsgi/

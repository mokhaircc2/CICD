**CI/CD using GitHub and AWS CodeDeploy**
!#/bin/bash
#install Apache
yum update httpd -y
systemctl start httpd
systemctl enable httpd

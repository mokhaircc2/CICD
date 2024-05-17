**CI/CD using GitHub and AWS CodeDeploy**


Follow the documentation from the link below</b>

https://medium.com/@mokhaircc2/ci-cd-using-github-and-aws-4daac8a131f1


In this project I will create a multi-environment pipeline to deploy applications to a Dev and Prod environment using EC2 instances, CodeDeploy, CodePipeline and GitHub. I will be using Visual Studio Code to push any updates locally to our remote repository.

From the AWS console Launch 2 instances (Amazon Linux2, t2.micro), name them Dev and Prod and attach instance profile (role for CodeDeploy) to EC2. On the User data script configure the installation of Apache and CodeDeploy agent:

#!/bin/bash<br />

#install Apache webserver<br />
yum update -y<br />
yum install httpd -y<br />
systemctl start httpd<br />
systemctl enable httpd<br />

#install CodeDeploy agent<br />
yum install ruby -y<br />
yum install wget -y<br />
wget https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install<br />

#Amazon S3 bucket contains the CodeDeploy Resource Kit files for your region, and region-identifier is the identifier for your region. For a list of bucket names and region identifiers see Resource kit bucket names by Region on the AWS documentation.<br />

#To execute permissions on the install file:<br />
chmod +x ./install<br />

#To install the latest version of the CodeDeploy agent:<br /> 
./install auto<br />

#Copy the public DNS name of the EC2 instance and paste it to the browser to view custom message of index.html file<br />


<b>User Data Script</b>

#!/bin/bash<br />

yum update -y<br />
yum install httpd -y<br />
systemctl start httpd<br />
systemctl enable httpd<br />
yum install ruby -y<br />
yum install wget -y<br />
wget  https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install<br />
chmod +x ./install<br />
./install auto<br />

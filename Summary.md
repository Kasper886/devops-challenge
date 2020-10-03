For this task I used Linux Ubuntu on VirtualBox.
I already had GitHub and Docker hub accounts.
 
1. The first of all I installed AWS CLI to manage AWS.

2. Installed Docker, Docker-compose and Git from official documentation.
https://docs.docker.com/engine/install/ubuntu/
https://docs.docker.com/compose/install/

3. Cloned the repository from https://github.com/prodopsio/devops-challenge to my Linux and then downloaded files to my GitHub https://github.com/Kasper886/devops-challenge

4. Authorized in AWS CLI by means of keys exporting:
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**********
export AWS_DEFAULT_REGION=us-east-1

5. Made the table description to check the type of variables:
aws dynamodb describe-table --table-name devops-challenge

6. Got the required item by means of the next command:
aws dynamodb get-item --table-name devops-challenge --key '{"code_name": {"S": "thedoctor"}}'

{
    "Item": {
        "code_name": {
            "S": "thedoctor"
        },
        "secret_code": {
            "S": "JHgT2xjDi9Xut8dZx8jdFYWi=ahkL*"
        }
    }
}

7. Synchronized Drone.io with Git

8. Downloaded the CentOS Docker container from the official Docker website:
sudo docker pull centos:latest

9. Started the container:
sudo docker run -it --name myWebserver centos:latest

10. Installed Apache
yum update 					#update the repository
yum install httpd -y		#install web service
yum install nano -y			#install nano text editor
nano /var/www/index.html 	#add the content from DynamoDB
exit						#exit from the container

11. Container Commit
sudo docker commit Mywebserver kasper86/devops-challenge:Apache2 

12. Run Apache2 with 5000 port
sudo docker run -p 5000:80 kasper86/devops-challenge:Apache2 /usr/sbin/httpd -D FOREGROUND

13. Push container to Docker hub
sudo docker push kasper86/devops-challenge:Apache2

 

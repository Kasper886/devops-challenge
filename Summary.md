For this task I used Linux Ubuntu EC2 AWS virtual server with SSH security group (port 22).
I already had GitHub and Docker hub accounts.
 
1. The first of all I installed AWS CLI to manage AWS.

2. Then I installed Docker and Git.

3. Then I cloned the repository from https://github.com/prodopsio/devops-challenge to my Linux and then downloaded files to my GitHub https://github.com/Kasper886/devops-challenge

4. I authorized in AWS CLI by means of keys exporting:
export AWS_ACCESS_KEY_ID=**************
export AWS_SECRET_ACCESS_KEY=**********
export AWS_DEFAULT_REGION=us-east-1

5. I made the table description to check the type of variables:
aws dynamodb describe-table --table-name devops-challenge

6. I've got the required item by means of the next command:
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



 
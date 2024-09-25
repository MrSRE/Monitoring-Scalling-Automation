# Monitoring-Scalling-Automation

```
1. Web Application Deployment: 

 - Use `boto3` to: 

 - Create an S3 bucket to store your web application's static files. 

 - Launch an EC2 instance and configure it as a web server (e.g., Apache, Nginx).  - Deploy the web application onto the EC2 instance. 

2. Load Balancing with ELB: 

 - Deploy an Application Load Balancer (ALB) using `boto3`. 

 - Register the EC2 instance(s) with the ALB. 

3. Auto Scaling Group (ASG) Configuration: 

 - Using `boto3`, create an ASG with the deployed EC2 instance as a template. 

 - Configure scaling policies to scale in/out based on metrics like CPU utilization or network traffic. 

4. SNS Notifications: 

 - Set up different SNS topics for different alerts (e.g., health issues, scaling events, high traffic). 

 - Integrate SNS with Lambda so that administrators receive SMS or email notifications. 

5. Infrastructure Automation: 

 - Create a single script using `boto3` that: 

 - Deploys the entire infrastructure. 

 - Updates any component as required. 

 - Tears down everything when the application is no longer needed. 

```

## Steps

1. First update required values in values.yaml file
2. execute app.py file, it will take values from values.yaml file, initially script will check resorces is there or not, if there it will use exiting else create new one.
3. Once script completely executed all resources id will store in resources.json file
4. By json and delete.py file delete all resources.

### app.py file explaination
1. creating s3 bucket
2. creating security group
3. creating ec2 instance and install nginx 
4. Creating Load balancer and Targeting groups
5. Register EC2 Instances with Target Group
6. Creating Listners for LB
7. Create Launch-templete for ASG
8. Creating Auto Scaling Group using previously created launch templete
9. Creating dynamic scaling policy for in/out
10. Create SNS Topic for Alert
11. Subscribe to SNS Topic
12. Publish Message to SNS Topic

all this steps were created using functions, by using deploy_web_application() function calling above resources to create.

by using sns-lambda.py can integrate sns to lambda function to send notifications

once app.py is executed all resources id will store in resources.json file,  by using json, delete.py file delete all resources

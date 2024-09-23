# Deploy-Web-App-With-Elatic-BeanStalk
AWS Elastic Beanstalk is a platform-as-a-service (PaaS) that allows you to deploy and manage web applications without worrying about the underlying infrastructure. It automatically handles tasks like provisioning servers, load balancing, scaling, and monitoring. Elastic Beanstalk supports multiple languages, including Python, Node.js, Java, Ruby, .NET, and PHP.
## OBJECTIVES
## DEPLOYMENT PROCEDURE
**Assuming you already have a simple web app**
* Login to AWS Management Console
* Navigate to AWS Elastic BeanStalk using the Search bar
* In the AWS Console under Elastic Beanstalk, click Create Application.
* Application Name: Give your application a name
* Platform: Choose your platform depending on your app. Platform branch and Platform version are automatically filled based on your choice of Platform![Screenshot (780)](https://github.com/user-attachments/assets/42847390-fa4c-4826-9b7d-fe5a6f86c82b)
* Under Application Code, choose Upload your code.
* Upload the zip file that contains your web application.Scroll to the bottom and Click Next ![Screenshot (781)](https://github.com/user-attachments/assets/2c064f84-afbd-4c11-abb3-03ecb19a305d)
**Configure Service Access**
* Create and use a new Service Role or Use an existing role or use the default role; aws-elasticebeanstalk-service-role
* Choose an EC2 key pair if available
**EC2 Instance Profile**
This is very important in the deployment process. If this is not correctly configured, the deployment process would throw an error at the end. below are the steps to creating an EC2 Instance profile.
**Preferably open AWS Management Console in a new tab to set up Instance Profile to avoid cancelling the progress thus far**
1. Go to the IAM Console
2. In the left navigation pane, click on Roles, then click on Create Role.
3. On the "Select trusted entity" page, under Trusted entity type, choose AWS service.
4. Then, select EC2 (since the role will be used by EC2 instances running under Elastic Beanstalk) under use case.
5. Click Next.
6. In the Attach policies section, search for and select the following managed policies:
 **AWSElasticBeanstalkWebTier**
 **AWSElasticBeanstalkWorkerTier**
 **AWSElasticBeanstalkMulticontainerDocker**
Optionally, you can add **CloudWatchLogsFullAccess** if your application needs access to log services.
Click Next.
7. Name the role
8. Click Create role to finish the process.
* Return to the previous tab, refresh and select the IAM Role created for Instance Profile and Click Next.
* Optionally Set up networking, database, and tags or Select the Defaults.
* Scroll down and Click Next.
* 

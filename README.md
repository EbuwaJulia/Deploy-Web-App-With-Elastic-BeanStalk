# Deploy-Web-App-With-Elatic-BeanStalk
AWS Elastic Beanstalk is a platform-as-a-service (PaaS) that allows you to deploy and manage web applications without worrying about the underlying infrastructure. It automatically handles tasks like provisioning servers, load balancing, scaling, and monitoring. Elastic Beanstalk supports multiple languages, including Python, Node.js, Java, Ruby, .NET, and PHP.
## OBJECTIVES
* AWS Elastic Beanstalk
* Deployment basics
* Environment management.
## DEPLOYMENT PROCEDURE
**Assuming you already have a simple web app**
* Login to AWS Management Console
* Navigate to AWS Elastic BeanStalk using the Search bar
* In the AWS Console under Elastic Beanstalk, click ***Create Application***.
* Application Name: Give your application a name
* Platform: Choose your platform depending on your app. ***Platform branch*** and ***Platform version*** are automatically filled based on your choice of Platform![Screenshot (780)](https://github.com/user-attachments/assets/42847390-fa4c-4826-9b7d-fe5a6f86c82b)
* Under Application Code, choose ***Upload your code***. (If you do not have a Simple web app, you can click on Sample Application)
* Upload the zip file that contains your web application.Scroll to the bottom and Click ***Next*** ![Screenshot (781)](https://github.com/user-attachments/assets/2c064f84-afbd-4c11-abb3-03ecb19a305d)
  
**Configure Service Access**
* Create and use a new ***Service Role*** or Use an existing role or use the default role; aws-elasticebeanstalk-service-role
* Choose an ***EC2 key pair***.
  
**EC2 Instance Profile**
This is very important in the deployment process. If this is not correctly configured, the deployment process would throw an error at the end. Below are the steps to creating an EC2 Instance profile.
**Preferably open AWS Management Console in a new tab to set up Instance Profile to avoid cancelling the progress thus far**
1. Go to the IAM Console
2. In the left navigation pane, click on ***Roles***>***Create Role***.
3. On the "Select trusted entity" page, under Trusted entity type, choose AWS service.
4. Then, select ***EC2*** (since the role will be used by EC2 instances running under Elastic Beanstalk) under use case.
5. Click ***Next***.
6. In the Attach policies section, search for and select the following managed policies:
 **AWSElasticBeanstalkWebTier**
 **AWSElasticBeanstalkWorkerTier**
 **AWSElasticBeanstalkMulticontainerDocker**
Optionally, you can add **CloudWatchLogsFullAccess** if your application needs access to log services.
Click ***Next***.
7. Name the role
8. Click ***Create role*** to finish the process.
* Return to the previous tab, refresh and select the IAM Role created for Instance Profile and Click Next.
* Optionally Set up networking, database, and tags or Select the Defaults.
* Scroll down and Click ***Next***.
  
**Configure instance traffic and scaling**
* Instances and CloudWatch monitoring should be left as Default
* Under EC2 Security groups, Select an EC2 security that you have configured to allow incoming traffic on ***ports 80, 443, 22 and 8080***.
* Scroll down and click ***Next***.
* Under Health Reporting System, Select ***Basic***
* Optionally unselect Activated Managed Updates
* Scroll down and Click on ***Next***.
* Review Settings and Click ***Submit***
* Wait few minutes for the environment to be launched.![Screenshot (782)](https://github.com/user-attachments/assets/34ccefa5-bdfa-4857-801a-adf1ec738a17)
* The above creates underlying Instance ![Screenshot (783)](https://github.com/user-attachments/assets/b9ce03e9-aa92-4233-97b4-c12d05bdc603)
  
**Configure the Elastic Beanstalk Environment**
* Load Balancer and Auto-scaling Configuration (optional):
  1.  Once your environment is up and running, click on ***Configuration*** in the left menu.
  2.  Under Instance traffic and Scaling click ***Edit*** to adjust the number of instances in the auto-scaling group under Capacity. You can configure the minimum and maximum number of instances.
  3.  Under Load Balancer, you can adjust settings like enabling sticky sessions or switching between Application Load Balancer and Classic Load Balancer.
      
**Access Your Application**
* Once Elastic Beanstalk finishes deploying your app, it will provide a ***URL***. You can find this in the ***Environment Dashboard*** under Environment URL.
* Open the URL to access your application.
  
**Manage Your Application: Deploy New Versions:**
* If you make changes to your application code and need to redeploy, go back to the Elastic Beanstalk console.
* In your environment dashboard, click Upload and Deploy.
* Upload the new version of your application zip file, then click Deploy.
  
**Terminate the Environment**
* If you no longer need the environment and want to avoid costs, go back to your Environment Dashboard.
* Click Actions, then select ***Terminate Environment***.
* Confirm the termination. Elastic Beanstalk will remove all resources associated with the environment, including EC2 instances, load balancers, and auto-scaling groups.

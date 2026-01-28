# 1. Jenkins CI CD pipeline for flask application  
## Objective: Set up a Jenkins pipeline that automates the testing and deployment of a simple Python web application.   

### Requirements:    
### 1. Setup:    
   - Install Jenkins on a virtual machine or use a cloud-based Jenkins service.  
   - Configure Jenkins with Python and any necessary libraries.  
     <img width="613" height="92" alt="image" src="https://github.com/user-attachments/assets/3f4b8670-835d-42c8-8dad-8ea32e78901a" />  
     <img width="660" height="420" alt="image" src="https://github.com/user-attachments/assets/42859373-2e7c-4a56-b205-e10bc2971e58" />  
     <img width="533" height="60" alt="image" src="https://github.com/user-attachments/assets/dd0cea93-3fac-491c-b37a-861ea38861e8" />  
     <img width="1410" height="343" alt="image" src="https://github.com/user-attachments/assets/0027952f-66d0-4398-ba7e-21c70d54c252" />  
     <img width="432" height="72" alt="image" src="https://github.com/user-attachments/assets/7f379e43-eedb-46b4-9124-ced366384f72" />  
     
### 2. Source Code:  
   - Fork the provided Python web application repository on GitHub (provide a link to a sample Python web application repository).    
     <img width="297" height="72" alt="image" src="https://github.com/user-attachments/assets/bd48b017-4f2e-4912-911a-4b66d7175d46" />    
   - Clone the forked repository into your Jenkins server.  
     <img width="621" height="116" alt="image" src="https://github.com/user-attachments/assets/f545f647-a1bb-4a44-8840-f3cb42a888b8" />

### 3. Jenkins Pipeline:  
   - Create a Jenkinsfile in the root of your Python application repository.  
   - Define a pipeline with the following stages:  
   - Build: Install dependencies using pip.    
   - Test: Run unit tests using a testing framework like pytest.      
   - Deploy: If tests pass, deploy the application to a staging environment.  
     <img width="654" height="642" alt="image" src="https://github.com/user-attachments/assets/fb308765-0bbb-4133-9bb9-7d8bf5311ac6" />  

### 4. Triggers:  
   - Configure the pipeline to trigger a new build whenever changes are pushed to the main branch of the repository.  
     <img width="989" height="691" alt="Screenshot 2026-01-28 at 6 24 23 PM" src="https://github.com/user-attachments/assets/003375a9-3639-4cd6-b49d-c2899f83b667" />  
     <img width="845" height="627" alt="image" src="https://github.com/user-attachments/assets/e6a5846a-b47b-4f47-8367-1d0b4a76bf32" />  

### 5. Notifications:  
   - Set up a notification system to alert via email when the build process fails or succeeds.  

     I am using AWS SNS for the email setup  
     Created a SNS topic with Email service  
     <img width="1227" height="378" alt="image" src="https://github.com/user-attachments/assets/1d673dc7-d214-48fa-9fce-5722d9605b42" />  
     
     Created a IAM role to attach to the EC2 instance where jenkins is running and added the SNSFull access to the role.  
     <img width="1219" height="480" alt="image" src="https://github.com/user-attachments/assets/ba790a83-075a-410b-a495-151d3a2f640e" />  

     Added the below block to the Jenkinsfile  
     <img width="556" height="284" alt="image" src="https://github.com/user-attachments/assets/2a3340ce-4456-448e-80c0-7cb09a5c7dfd" />  
  
     When the build succeeded I received the below email  
     <img width="1125" height="271" alt="image" src="https://github.com/user-attachments/assets/c408d98c-22c3-4161-b2b2-717ea8a517e6" />  
     <img width="487" height="158" alt="image" src="https://github.com/user-attachments/assets/5523eb75-068d-4203-9ea6-bd3724e9cd2d" />  
       
  
     When the build failed I received the below email    
     <img width="1121" height="265" alt="image" src="https://github.com/user-attachments/assets/e48b68e3-247a-4d89-86c9-94c6b258bc06" />  
     <img width="391" height="169" alt="image" src="https://github.com/user-attachments/assets/bd78c200-a7c4-48e7-8c3d-242d406da993" />  
       
    
# 2. GitHub Actions CI/CD Pipeline Flask App  
## Objective: Implement a CI/CD workflow using GitHub Actions for a Python application.   

### Requirements:  
### 1. Setup:  
   - Use a provided Python application repository on GitHub (provide a link to a sample Python application repository).  
   - Ensure the repository has a main branch and a staging branch.  
     <img width="996" height="670" alt="Screenshot 2026-01-19 at 9 05 45 PM" src="https://github.com/user-attachments/assets/ae922d37-1746-48a3-8a20-831352e171df" />  
     <img width="1323" height="379" alt="image" src="https://github.com/user-attachments/assets/4929f32a-1748-4978-8c9b-e5794b9aff27" />  
    
    
### 2. GitHub Actions Workflow:  
   - Create a .github/workflows directory in your repository.  
   - Inside the directory, create a YAML file to define the workflow.  
     <img width="961" height="599" alt="image" src="https://github.com/user-attachments/assets/0ab44963-54b3-44e2-9723-1967708816e1" />     

### 3. Workflow Steps:  
   - Define a workflow that performs the following jobs:    
   - Install Dependencies: Install all necessary dependencies for the Python application using pip.  
     First we are checking out all the files to the runner, installing python in runner and then installing the dependencies mentioned in requirements.txt  
     <img width="323" height="406" alt="image" src="https://github.com/user-attachments/assets/a16e6270-1fd1-458f-9624-3e91fb36fa6f" />  
  
   - Run Tests: Execute the test suite using a framework like pytest.  
     <img width="391" height="115" alt="image" src="https://github.com/user-attachments/assets/6e894242-dae7-4ee5-856b-caadfbca91d3" />  
  
   - Build: If tests pass, prepare the application for deployment.  
     In this step we have first written the dockerfile, then built the image.  
     <img width="399" height="230" alt="image" src="https://github.com/user-attachments/assets/dca034d6-104d-4b02-8fe1-b0feee91ce50" />  
     <img width="214" height="60" alt="image" src="https://github.com/user-attachments/assets/61afc681-78ca-4fa8-8e97-0d4814fe1e12" />  
  
   - Deploy to Staging: Deploy the application to a staging environment when changes are pushed to the staging branch.  
     <img width="640" height="223" alt="image" src="https://github.com/user-attachments/assets/2ce0d952-0043-4287-80b5-6fb172f9369b" />  
     <img width="272" height="513" alt="image" src="https://github.com/user-attachments/assets/09d9de86-27a8-4b32-b3c0-29124dc1a5e2" />  
  
   - Deploy to Production: Deploy the application to production when a release is tagged.  
     We will first raise a PR and get the main branch merged with staging branch. Once merging done, we will publish a release and hence the production yaml file will get triggered.  
     Trigger here is when the release is published.  
     <img width="714" height="246" alt="image" src="https://github.com/user-attachments/assets/33762cf5-2f61-49a9-9e84-e2a412f6ee22" />  
     <img width="925" height="351" alt="image" src="https://github.com/user-attachments/assets/8ce57df8-5f83-4eeb-aba5-410d7c473d7c" />    
     <img width="598" height="555" alt="image" src="https://github.com/user-attachments/assets/14e98c8b-75bf-4468-b5d4-cc7833ed1335" />   
     <img width="277" height="488" alt="image" src="https://github.com/user-attachments/assets/dec92d26-19e0-436e-9bc2-da706b9064a7" />
         
### 4. Environment Secrets:  
   - Use GitHub Secrets to store sensitive information required for deployments (e.g., deployment keys, API tokens).  
     I have used Environment variables to store mongo db uri and secrets to store the secret key in two diff environments.  
     Staging - all  
     Production - production  
     <img width="606" height="709" alt="image" src="https://github.com/user-attachments/assets/7531d66e-d7f0-418f-a032-f1a79e3c91dc" />  
     <img width="598" height="716" alt="image" src="https://github.com/user-attachments/assets/fc2d6830-03b1-4db8-bc87-4cb48372cc2d" />  


       

       
       

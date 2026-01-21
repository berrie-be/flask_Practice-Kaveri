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


       

       
       

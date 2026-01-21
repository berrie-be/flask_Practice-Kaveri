# 2. GitHub Actions CI/CD Pipeline Flask App  
## Objective: Implement a CI/CD workflow using GitHub Actions for a Python application.   

Requirements:  
1. Setup:  
   - Use a provided Python application repository on GitHub (provide a link to a sample Python application repository).  
   - Ensure the repository has a main branch and a staging branch.  
     <img width="996" height="670" alt="Screenshot 2026-01-19 at 9 05 45 PM" src="https://github.com/user-attachments/assets/ae922d37-1746-48a3-8a20-831352e171df" />  
     <img width="1323" height="379" alt="image" src="https://github.com/user-attachments/assets/4929f32a-1748-4978-8c9b-e5794b9aff27" />  
  
  
2. GitHub Actions Workflow:  
   - Create a .github/workflows directory in your repository.  
   - Inside the directory, create a YAML file to define the workflow.  
     <img width="961" height="599" alt="image" src="https://github.com/user-attachments/assets/0ab44963-54b3-44e2-9723-1967708816e1" />   

3. Workflow Steps:  
     - Define a workflow that performs the following jobs:  
     - Install Dependencies: Install all necessary dependencies for the Python application using pip.    
       <img width="306" height="260" alt="image" src="https://github.com/user-attachments/assets/d78c1657-57e9-4a0c-845f-bb473455a97a" />  

     - Run Tests: Execute the test suite using a framework like pytest.  

     - Build: If tests pass, prepare the application for deployment.  

     - Deploy to Staging: Deploy the application to a staging environment when changes are pushed to the staging branch.  

     - Deploy to Production: Deploy the application to production when a release is tagged.  

# SonarQube integration in GitLab CICD + AWS EKS | End-to-End Project

<div align="center">
   <img src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/f4f3d837-197d-4428-8f65-90f6057ad19c" title="SonarQube" alt="SonarQube" width="40" height="40"/>&nbsp;➕&nbsp;
</div>


Objectives:

- ☑️ Push a working Python Flask app to Gitlab repository
- ☑️ Make sure SonarQube server is up and running
- ☑️ Create working CI/CD pipeline:
  - ✔️ Developer create pull request
  - ✔️ GitLab CI/CD pipeline will trigger and run jobs
    - 🏁 Run Test job
    - 🏁 Run Sonar Qube scan job
    - 🏁 If no failure, build docker image and push to DockerHub
- ☑️ Deploy python Flask webapp to AWS Elastic Kubernetes
- ☑️ See demo run through



## 1) Push a working Python Flask app to Gitlab repository

The working sample repository is found here: [my GitLab repo](https://gitlab.com/kyleyap/sonarqube_cicd_gitlab)

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/c09c3dff-34d4-4dfa-b00e-cf32095ea1d2">
</p>

## 2) Make sure SonarQube server is up and running

I used my previous project [SonarQube on Docker compose](https://github.com/famasboy888/SonarQube_docker)

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/6263af74-5b85-4cc0-bb6b-b9552705c3a2">
</p>


## 3) Create working CI/CD pipeline:

CI/CD pipeline will only trigger when there is a Merge Request to `main` branch.

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/80d70071-91b6-406c-a817-6c253fac2d87">
</p>

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/7b8976f5-e868-4ad4-aabc-4f456072983f">
</p>

If fails, it will still send report to Sonar Qube server but it won't continue building the Docker image

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/061b3924-43ba-4707-961f-4a32ed79688b">
</p>

## 4) Deploy python Flask webapp to AWS Elastic Kubernetes

We will deploy our Flask Webapp in EKS via ArgoCD.

Notice that we can access ArgoCD by using LoadBalancer generated DNS.

After creation of Project from ArgoCD, it will create a another LoadBalancer service for our Flask App. 

We will be able to access our Flask webapp from the newly generated DNS.

<p align="left">
  <img width="100%" height="100%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/36cb2d9a-456d-4330-b09d-97bd8ed61069">
</p>

---

# Demo - full run through of the Pipeline

🏁 Our goal is to see our code changes reflect **seamlessly** to the live web application.

Currently, this is how our Flask app looks like. We will change **GitLab CI/CD demo webapp** > **GitLab CI/CD demo webapp + AWS EKS** and add some cool picture after.

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/16f5632f-d834-43e1-8afc-4b828fd02d6e">
</p>

Since this a run through, we will try to simulate a real codde change in a project. Will will follow the following flow:

➡️ Flow:
- Create an Issue in GitLab and create feature branch

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/24b36eb4-7131-46c0-b876-3b40959079ba">
</p>
  
- Address the issue (we will modify the code) and Push to feature branch

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/d9655cd0-e9f8-48b3-935a-9c5f9fb4e695">
</p>
  
- Create Merge request to main branch

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/35de8b50-9432-4f2b-b47a-f6f422baf581">
</p>

- Let the pipeline run and do it's magic. We can also check that reports were displayed in our SonarQube server.

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/2eb23a92-85e4-4109-84be-a36121c984d4">
</p>
  
- Confirm the changes

<p align="left">
  <img width="50%" height="50%" src="https://github.com/famasboy888/GitLab_CICD_SonarQube_AWS_EKS/assets/23441168/58fd657d-6ac2-4fe5-9900-27564d085224">
</p>


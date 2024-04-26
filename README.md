# SonarQube integration in GitLab CICD + AWS EKS | End-to-End Project

Objectives:

- ☑️ Push a working Python Flask app to Gitlab repository
- ☑️ Make sure SonarQube server is up and running
- ☑️ Create working CI/CD pipeline:
  - ✔️ Developer create pull request
  - ✔️ GitLab CI/CD pipeline will trigger and run jobs
    - 🏁 Run Test job
    - 🏁 Run Sonar Qube scan job
    - 🏁 If no failure, build docker image and push to DockerHub
- ☑️ Deploy python Flask webapp to AWS Elastic Kubernetes:
  - ✔️ ArgoCD will listen to changes from Main branch
  - ✔️ ArgoCD will redeploy to EKS using Helm chart



## 1) Push a working Python Flask app to Gitlab repository

The working sample repository is found here: [my GitLab repo](https://gitlab.com/kyleyap/sonarqube_cicd_gitlab)

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/dd582884-ac1c-4fad-949d-07e9e8aea5a3">
</p>

## 2) Make sure SonarQube server is up and running

## 3) Create working CI/CD pipeline:

It will still send report to Sonar Qube server but it won't continue building the Docker image

<p align="left">
  <img width="80%" height="80%" src="https://github.com/famasboy888/SonarQube_GitLab_CICD/assets/23441168/061b3924-43ba-4707-961f-4a32ed79688b">
</p>


## 4) During Failure

## 5) Deploy python Flask webapp to AWS Elastic Kubernetes



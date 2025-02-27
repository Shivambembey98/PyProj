1 . Developing the Python CLI Application

A simple Python CLI-based calculator application was developed.

The application does not use any external libraries and only relies on basic Python functionalities.

Unit tests were written using Python's unittest module to ensure the correctness of the program.

2 . Containerizing the Application with Docker

A Dockerfile was created to containerize the application.

The Dockerfile defines the base image, copies the application code, and specifies the command to run the application inside a container.

The Docker image was built and tested locally using:

docker build -t python-cli-app .
docker run -it python-cli-app

3 . Setting Up GitHub Actions for CI/CD

A GitHub Actions workflow file (.github/workflows/cicd.yml) was created to automate testing, building, and deployment.

The pipeline consists of three jobs:

Test - Runs unit tests on every code change.

Build - Builds a Docker image of the application.

Deploy - SSHs into an AWS EC2 instance and deploys the application.

4 . Deploying the Application on AWS EC2

An EC2 instance was set up with Docker installed.

SSH access was configured using GitHub Secrets for secure deployment.

The GitHub Actions pipeline automates the following steps on EC2:

Pull the latest changes from GitHub.

Stop and remove any running container.

Build and run the new container.

5. Manual Workflow Dispatch

Instead of triggering the workflow on push events, workflow_dispatch was used to manually trigger the pipeline.

This allows for controlled deployment, ensuring that changes are only applied when explicitly triggered.








Steps to Run and Test the Application

1 . Clone the Repository

2 . Create an ec2 instance and note down following things 
  i) host public ip
  ii) username (instance type like ubuntu)
  iii) private key (pem file)

3. now in github actions secret section make secrets for all of the above mentioned
4. we made the workflow manual using workflow dispatch in yml file, so go to actions tab then select workflow and then run workflow
5. the python application , docker and all the dependencies will be downloaded the mentioned ec2
6. the images will automatically be build
7. use docker images command to check the image name then
8. run the container to use the python calculator application

  


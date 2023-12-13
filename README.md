# Welcome to the final exam CLCM 3504 repository.
Here is how it works
![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/941b771a-4a8f-4bfb-ac79-5837755878db)


## Explaining the diagram
1. A user update this repo.
2. A Github Actions pipeline deploy the changes inside an EC2 instance
3. A custom script is executed which reset the environment and run docker instructions.
4. Dockerfile and Docker-compose files are executed to create a new image, publish it in DockerHub and run it.
5. The image is publicly available in DockerHub (With an account) and the site exposed in EC2 with a container.
6. **_All involucred parts smiles._**

_Dockerhub images created can be found here: https://hub.docker.com/repository/docker/gerardo0579bvc/clcm3504-finalexam-image_


# I am not the owner, how can I use it.

Of course, you have two options.
1) Ask for rights to this repo or,
2) Create your own environment based on this one

## 1) Asking for rights to this repo
If you ask for rights on this repo, you just need to verify the EC2 instance is running to avoid issues. Then, you can have fun updating this repo and watching the changes in the public url and DockerHub, like this!

![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/1740c0ad-24bd-4a5b-a6e0-a30fe6ca3b34)


## 2) Configure your own environment based on this one.
Wheter you want fork this project or create your own, you can follow this instructions to make it work.

### 1. Preparing our EC2.
Setup and apply a terraform project to create your EC2 instance with Linux2 AMI. Don't forget to open ports 22 and 80. Your terraform file should looks similar to this one.

![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/d47fdeb7-b211-4cdd-8ce1-0ba950a6211d)

### 2. Setup your EC2 packages.
Congratulations! This project is ready to configure your environment as long as your instance is the right one and the ports are open. :)

### 3. Prepare your repository
No matter what you decide, you just need to ensure 3 simple things are inside your repo.
    1. The website
    2. The docker-compose.yml file.
    3. Prepare your .github/workflows/main.yml to host the pipeline

***If you are using your own site and settings/accounts, be aware some adjusments will be required***

![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/ac554b69-f12d-45ef-aa34-818c501a5796)

### 4. Prepare Env secrets inside your GitHub repo.
Verify the repository have the right secrets and values configured. In the next image you can verify the names (but we CANNOT guarentee different values are okay).
![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/a12fac84-e9a1-4145-be99-d836639a57ec)

### 5. Set the pipeline
If you forked this project, the pipeline should be set. If not, you can reuse this repository pipeline for your own repository.
It is ready to install required dependencies but you may need to configure your DockerHub account, directories paths and some other things.

### 6. Execute the pipeline
If you followed all the steps, everytime push a commit a pipeline must be executed. It will update the files, create and tag a new image, start a container from it and push the image to DockerHub.

# Proof of work
The following image are screenshots of different successful tasks that were performed by the Github action piepeline automatically 

![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/9e432ca6-b382-4fc8-81e9-9773c2ad0ca6)

# Overcoming challenges
Of course, multiple challenges arised during the creation of this project. Here is a quick overview of them and their solutions.

## 1. Ensuring the host environment
To ensure the best experience for users of this project, ensuring the right EC2 environment required a lot of configuration with bash. Setting the rights directories, installing dependencies, login into account and executing files. A test repo was created were multiple changes on the pipeline were done to ensure it works just right.

![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/3328845d-1c64-45b8-bcb9-483829224a10)

## 2. Pushing an image to DockerHub
This required the setup of a new env variable, login into Docker account and managing version number with a new extra envfile.

![image](https://github.com/Gerardo0579-bvc/clcm3504-finalexam-repo/assets/144280594/9549dda0-71e8-4642-9360-f4f03d81bf80)

## 3. Using Docker compose
Not a really big issue though. This only required a bit of investigation on its purpose and how to use to take advantage of it

## 4. Making it all work together
As already shown with the amount of pipeline executions for testing. Achieving full integration of all files and apps required a lot of verifications and testing. The hardest part of course was to track any issue with the logic and fixing it to ensure its working.



## Requirements and Instructions
Specifies all requirements to run the discord bot

Prerequisites

* [Python](https://www.python.org)
* [Docker](https://www.docker.com/)
* [Amazon EKS](https://aws.amazon.com/eks/)

Upgrade pip:
```
python -m pip install --upgrade pip;
```
To clone the project from the repository:
```
git clone git@github.com:vishnuchalla007/chat-defender-bot.git
```
Setup amazon EKS cluster by following the below steps
```
https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html
```
Once the setup is done, place the token in bot.env and place the toxic_model.sav from the below link in data folder
```
https://drive.google.com/file/d/1NY3mEogwXqsz2SaNz-hC2r5a5HYp6M66/view?usp=sharing
```
After cloning, go to the folder in the terminal and build a Docker Image using below command
```
docker-compose build 
```
The above command would build 3 docker containers: 1 bot container, 1 database container and 1 daemon container. Inorder to start the discord bot
we need to execute.
```
docker-compose up 
```
Inorder to bring the bot offline. We just need to bring down all the containers using
```
docker-compose down 
```

NOTE: The current toxify model uses a python library called detoxify. Detoxify Currently doesnt support Apple Silicon. Apple Silicon users are advised to run the application using the docker. 

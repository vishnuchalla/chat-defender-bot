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
Our AWS Account login details to access cluster
```
username: sponnur@ncsu.edu
password: segroup41@fall
```
Once the setup is done, place the token in bot.env and place the toxic_model.sav from the below link in data folder
```
https://drive.google.com/file/d/1NY3mEogwXqsz2SaNz-hC2r5a5HYp6M66/view?usp=sharing
```
After cloning, go to the folder in the terminal and build a cross platform Docker Image using below command
```
docker buildx create --use; docker buildx build --platform linux/amd64,linux/arm64 --push -t vishnuchalla007/docker-se:latest .
```
Once that is done navigate to kubernetes folder and execute the below command.
```
kubectl apply -f *.yaml
```
Wait until all the pods come up into "Running" state by live monitoring using the below command
```
kubectl get pods -w 
```
The application should be up and running now. You can check logs of any pod using following command.
```
kubectl logs pod/<pod-name> -f
```
For a pod lifecycle description, execute the below command.
```
kubectl describe <pod-name>
```
To check all the resources. Execute the below command.
```
kubectl get all
```
To delete the resources. Use the same yaml resource files.
```
kubectl delete -f <file>.yaml
```
For more command explore kubernetes CLI: https://kubernetes.io/docs/reference/kubectl/

NOTE: The current toxify model uses a python library called detoxify. Detoxify Currently doesnt support Apple Silicon. Apple Silicon users are advised to run the application using the docker. 

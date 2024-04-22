# chest_xray_end_to_end

URLs from https://dagshub.com/genaiworks/chest_xray_end_to_end
MLFLOW_TRACKING_URI=https://dagshub.com/genaiworks/chest_xray_end_to_end.mlflow \
MLFLOW_TRACKING_USERNAME=genaiworks \
MLFLOW_TRACKING_PASSWORD=ec34733c1df0a2704cccff33c8adf2070636133f \
python script.py

```bash
export MLFLOW_TRACKING_URI=https://dagshub.com/genaiworks/chest_xray_end_to_end.mlflow 
export MLFLOW_TRACKING_USERNAME=XXXX
export MLFLOW_TRACKING_PASSWORD=ec34733c1df0a2704cccff33c8adf2070636133f 
```

 Login to AWS console.
2. Create IAM user for deployment
#with specific access

1. EC2 access : It is virtual machine

2. ECR: Elastic Container registry to save your docker image in aws


#Description: About the deployment

1. Build docker image of the source code

2. Push your docker image to ECR

3. Launch Your EC2 

4. Pull Your image from ECR in EC2

5. Lauch your docker image in EC2

 Create IAM policy Policy:
1. AmazonEC2ContainerRegistryFullAccess
2. AmazonEC2FullAccess

1 Log into the EC2 instance and run following commands
2  sudo apt update
3  clear
4  sudo apt install python3-pip
5  sudo pip3 install pipenv
6  sudo pip3 install virtualenv
7  mkdir mlflow
8  pipenv install mlflow
9  pipenv install awscli
10  pip install boto3
11  pipenv install boto3

   mlflow server -h 0.0.0.0 --default-artifact-root s3://mlflow-buc9

   Start MLflow
   http://ec2-3-191-150-14.us-west-1.compute.amazonaws.com:5000/

export MLFLOW_TRACKING_URI=http://ec2-3-191-150-14.us-west-1.compute.amazonaws.com:5000


GIT HUB SETUP

First Step: Checking if we already have the public SSH key.

Open Terminal.
Enter ls -al ~/.ssh to see if existing SSH keys are present:
Check the directory list to see if you already have a public SSH key. Default public is one of the following d_dsa.pub, id_ecdsa.pub, id_ed25519.pub, id_rsa.pub.

If you don't find then go to step 2 otherwise follow step 3

Step 2: Generating public SSH key

Open Terminal.
Enter the following command with a valid email address that you use for github ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
You will see the following in your terminal Generating public/private rsa key pair. When it prompts to"Enter a file in which to save the key," press Enter. This accepts the default file location. When it prompts to Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter] Just press enter again.
At the prompt, "Type a secure passphrase. Enter passphrase (empty for no passphrase): [Type a passphrase]" press enter if you don't want to Enter same passphrase again: [Type passphrase again] press enter again
This will generate id_rsa.pub

Step 3: Adding your SSH key to the ssh-agent

Interminal type eval "$(ssh-agent -s)"

Add your SSH key to the ssh-agent. If you are using an existing SSH key rather than generating a new SSH key, you'll need to replace id_rsa in the command with the name of your existing private key file. Enter this command $ ssh-add -K ~/.ssh/id_rsa

Now copy the SSH key and also add it to you github account

In terminal enter this command with your ssh file name pbcopy < ~/.ssh/id_rsa.pub This will copy the file to your clipboard Now open you github account Go to Settings > SSH and GPG keys > New SSH key Enter title and paste the key from clipboard and save it. Voila you're done.
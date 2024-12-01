## STEPS TO FOLLOW:
1. ensure aws is configured: `aws configure`
2. `aws ecr create-repository --repository-name <name>`
3. `docker tag <local image:imagetag> <ECR_REPOSITORY_URI>:latest`
4. `aws ecr get-login-password --region <AWS_REGION> | docker login --username AWS --password-stdin <ECR_REGISTRY>`
5. `docker push <ECR_REPOSITORY_URI>:latest`
6. need to setup the aws configure in ec2 as well to pull from ecr in docker compose file

To setup port running, go to security and add click on security groups. 
Go to inbound rules and add custom tcp rule with port <whichever port is exposed to localhost> and source is set as anywhere.
then run <public ip>:<port>

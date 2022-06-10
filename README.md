# Docker Local
1. docker pull itzg/minecraft-server
2. docker images
3. docker run -d -p 25565:25565 -e EULA=TRUE itzg/minecraft-server
4. docker ps
5. docker logs -f mc

# Dockerfile
1. docker build -t codebay_mc .

# AWS ECR
1. Create repo
2. aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin 106213279016.dkr.ecr.us-west-1.amazonaws.com/codebay_mc_ecs
3. docker tag codebay_react:latest 106213279016.dkr.ecr.us-west-1.amazonaws.com/codebay_mc_ecs:latest
4. docker push 106213279016.dkr.ecr.us-west-1.amazonaws.com/codebay_mc_ecs
5. aws ecr list-images --repository-name codebay_mc_ecs --region us-west-1

# AWS ECS
1. Create Cluster
2. On demand - t3.micro - vpc1 - subnet1

# Task
1. Create Task Definition
2. Select Task Policy with permissions to run ecr and ecs
3. Create Container definitionwith image from ecr and port mapping
4. Run task ec2 - taskDefinition
5. Security Group CustomTCP Port 25565

# Service
1. Create Service
2. Select task and name, minimum healthy percent 0
3. aws ecs update-service --cluster test --service React --force-new-deployment

# Azure
1. Select classic editor
2. Select repo
3. Docker container template
4. Trigger Enable continuous integration
5. Agent Specification x
6. Build an Image
7. Amazon ECR Push

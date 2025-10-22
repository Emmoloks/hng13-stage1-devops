HNG-DEVOPS ASSIGNMENT1
Task Objective
Develop a robust, production-grade Bash script that automates the setup, deployment, and configuration of a Dockerized application on a remote Linux server.

Task Breakdown

Your script (deploy.sh) should be a single, executable Bash file that performs all actions in sequence, with proper error handling, 
validation, and logging throughout.

1. Collect Parameters from User Input
Prompt for and validate:
Git Repository URL
Personal Access Token (PAT)
Branch name (optional; defaults to main)
Remote server SSH details:
Username
Server IP address
SSH key path
Application port (internal container port)

2. Clone the Repository
Authenticate and clone the repo using the PAT.
If it already exists, pull the latest changes instead.
Switch to the specified branch.

3. Navigate into the Cloned Directory
Automatically cd into the cloned project folder.
Verify that a Dockerfile or docker-compose.yml exists.
Log success or failure.

4. SSH into the Remote Server
Establish SSH connection with provided credentials.
Perform connectivity checks (ping or SSH dry-run).
Execute remaining commands remotely (ssh user@ip "commands...").

5. Prepare the Remote Environment
On the remote host:
Update system packages.
Install Docker, Docker Compose, and Nginx (if missing).
Add user to Docker group (if needed).
Enable and start services.
Confirm installation versions.

6. Deploy the Dockerized Application
Transfer project files (via scp or rsync).
Navigate to project directory.
Build and run containers (docker build + docker run or docker-compose up -d).
Validate container health and logs.
Confirm app accessibility on the specified port.

7. Configure Nginx as a Reverse Proxy
Dynamically create or overwrite Nginx config.
Forward HTTP (port 80) traffic to container’s internal port.
Ensure SSL readiness (optional self-signed cert or Certbot placeholder).
Test config and reload Nginx.

8. Validate Deployment
Confirm that:
Docker service is running.
The target container is active and healthy.
Nginx is proxying correctly.
Test endpoint using curl or wget locally and remotely.

9. Implement Logging and Error Handling
Log all actions (success/failure) to a timestamped log file (e.g., deploy_YYYYMMDD.log).
Include trap functions for unexpected errors.
Use meaningful exit codes per stage.

Do not use configuration management tools like Ansible or Terraform.
:W

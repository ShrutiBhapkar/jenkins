# Jenkins Pipeline: Docker Image Build and Deployment

This Jenkins pipeline script automates the build and deployment of a Docker image to Docker Hub and an EC2 instance.

## Prerequisites

- Jenkins CI/CD server configured with the necessary plugins.
- Docker installed on the Jenkins server.
- Docker Hub account and credentials.
- EC2 instance set up and accessible.

## Pipeline Stages

1. **Checkout:**
   - This stage checks out the source code from the specified GitHub repository.

2. **Test case:**
   - This stage installs the required dependencies and runs the test cases using pytest.

3. **Build Docker Image:**
   - This stage builds a Docker image using the specified Dockerfile and tags it with the Jenkins build ID.

4. **Push Docker Image to Docker Hub:**
   - This stage pushes the Docker image to Docker Hub using the provided Docker Hub credentials.

5. **Deploy Docker Image on EC2:**
   - This stage pulls the Docker image from Docker Hub.
   - It stops and removes any existing containers with the same name.
   - It runs a new container with the pulled Docker image on the specified port.

## Configuration

1. Set up Docker Hub credentials in Jenkins:
   - Go to Jenkins > Credentials > System > Global credentials (unrestricted).
   - Add your Docker Hub credentials with the ID "docker-hub-credentials".
   - Provide the username and password/token for your Docker Hub account.

2. Adjust the script to fit your requirements:
   - Modify the Git repository URL in the 'Checkout' stage to point to your own repository.
   - Adjust the commands within each stage as per your project's requirements.

3. Configure the EC2 instance:
   - Ensure that your EC2 instance is set up and accessible via SSH.

## Usage

1. Set up a Jenkins job with the pipeline script:
   - Create a new Jenkins job and select "Pipeline" as the job type.
   - Copy and paste the pipeline script into the Pipeline section of the job configuration.
   - Save the configuration.

2. Run the Jenkins job:
   - Trigger the job manually or set up a trigger based on your requirements.
   - The pipeline will execute the stages sequentially and perform the specified tasks.

## Notes

- Make sure to replace the placeholders and customize the script to fit your project's needs.
- This is a basic example, and you can modify the pipeline stages and tasks as per your requirements.


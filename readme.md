# Jenkins Pipeline for Docker Image Deployment

This Jenkins pipeline script automates the deployment of a Docker image to an EC2 instance using Docker Hub and webhook triggering.

## Prerequisites

- Jenkins installed and set up
- Docker Hub account with appropriate credentials
- Access to an EC2 instance with Docker installed

## Setup

1. Create Jenkins credentials:
   - Create a new set of credentials in Jenkins to access Docker Hub. Name it 'docker-hub-credentials' or a suitable name of your choice.
   - Add the Docker Hub username and password to the credentials.

2. Configure the container port:
   - Update the port number in the line `docker run -d --name my-container -p 5000:5000 shrutibhapkar/mainassignment:${env.BUILD_ID}` to the desired container port.

3. Set up the webhook:
   - In your version control system (GitHub in this case), navigate to the repository settings.
   - Add a webhook with the Jenkins URL followed by '/github-webhook/' as the payload URL.
   - Select the events to trigger the webhook (e.g., push events).

## Pipeline Steps

1. Checkout:
   - Clones the GitHub repository into the Jenkins workspace.

2. Test case:
   - Installs the required dependencies and runs the test cases using Pytest.

3. Build Docker Image:
   - Builds the Docker image using the Dockerfile in the 'assignment' directory.

4. Push Docker Image to Docker Hub:
   - Pushes the Docker image to Docker Hub using the provided credentials.

5. Deploy Docker Image on EC2:
   - Pulls the Docker image from Docker Hub.
   - Stops and removes any existing container with the name 'my-container'.
   - Runs a new container with the pulled Docker image on the specified container port.

6. Clean up:
   - Clean up any resources or perform any necessary cleanup tasks.

## Refer my credentials to access jenkins -
[pipeline](http://13.126.119.28:8080/job/pipeline%20assignment/)
Username-shruti
Password-user123
for container port deployed output-
[ouput](http://13.126.119.28:5000/)
## Notes

- Make sure to replace the placeholders in the script with the appropriate values.
- This is a basic example, and you can modify the script to meet your specific requirements.

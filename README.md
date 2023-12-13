# Integrated_API_Music_Recommendation_System

Simple Web Application that performs sentiment analysis on user-input text and suggests Spotify tracks based on the detected emotion. The application is implemented using HTML, JavaScript, AWS Comprehend for sentiment analysis and the Spotify API for music recommendations.

Before running the application, ensure that you have the following:

* AWS Account: Obtain AWS credentials (access key ID, secret access key) and specify the desired region in the config.js file.
* Spotify Developer Account: Create a Spotify Developer account, obtain client ID and client secret, and update the config.js file.
* Docker: Install Docker to easily containerize and deploy the application.


**Setting up the Environment**

1. Clone the repository:
* git clone https://github.com/Hemanth110500-projects/Integrated_API_Music_Recommendation_System.git

2. Navigate to the project directory

3. Update the **config.js** file with your AWS and Spotify credentials.


**Building and running the application with Docker**

Build the Docker image and run the container:

**docker build -t sentiment-analysis-demo .**
**docker run -p 8080:80 sentiment-analysis-demo**

**Deploying to Amazon ECS**

* Set up Amazon ECR Repository

**aws ecr create-repository --repository-name REPOSITORY_NAME**

* Authenticate Docker with ECR

**aws ecr get-login-password --region us-east-1 | docker login --username AWS password-stdin YOUR_AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com**

* Build, Tag, and Push Docker Image to ECR

**docker build -t REPOSITORY_NAME .**

**docker tag REPOSITORY_NAME:latest 826797162857.dkr.ecr.us-east-1.amazonaws.com/REPOSITORY_NAME:latest**

**docker push YOUR_AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com/REPOSITORY_NAME:latest**

* Verify ECR Image Pull

**docker pull YOUR_AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com/REPOSITORY_NAME:latest**

* Run the Deployed Image Locally

**docker run -p 8000:80 YOUR_AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com/REPOSITORY_NAME:latest**


The application will be accessible at http://localhost:8080 in your browser.

**Usage**
1. Open the web application in your browser.
2. Enter text in the provided textarea.
3. Click the "Analyze Sentiment" button to perform sentiment analysis.
4. View the sentiment result and receive Spotify track recommendations based on the detected emotion.
**Important Notes**
1. Ensure that your AWS and Spotify credentials are kept secure.
2. Adjust the sentiment-based keywords in the getKeywordsBySentiment function according to your preferences.
**Additional Information**
1. The sentiment analysis is powered by AWS Comprehend.
2. Spotify track recommendations are obtained through the Spotify API.
3. The application uses Nginx as the web server and is containerized for easy deployment.

* Feel free to customize and extend the application based on your requirements.


## Project: Automated CI Pipeline with Webhook

This project demonstrates how I set up an automated Continuous Integration (CI) pipeline using a webhook. Now, whenever I make changes to my project in Github, the pipeline in Jenkins is automatically triggered.

## Technologies Used

I used the following technologies in this project:

*   Jenkins
*   Github
*   Git
*   Docker
*   Java
*   Maven

## Project Description

Here's what I achieved in this project:

1. I integrated Github with Jenkins by installing the Github Plugin in Jenkins.

![github](https://github.com/Princeton45/jenkins-webhooks-trigger/blob/main/images/github-plugin2.png)

Then I configured the connection from Jenkins to Github in the Jenkins settings, making sure that credential `kind` was set to `secret` using an API token

![git-token](https://github.com/Princeton45/jenkins-webhooks-trigger/blob/main/images/git-token.png)


2. Webhook build trigger configuration

I went into one of my pipelines, then in the `configure` settings I checked the `GitHub hook trigger for GITScm polling` option.

![checked](https://github.com/Princeton45/jenkins-webhooks-trigger/blob/main/images/checked.png)

Then I went into my Github repository settings to create a webhook.

![webhook](https://github.com/Princeton45/jenkins-webhooks-trigger/blob/main/images/webhook.png)

Github will send notifications to the `/github-webhook/` endpoint on Jenkins when it detects a push to the branch. So now on every notification, Jenkins will trigger the pipeline.

On pushes to my `master` branch, the Jenkins `webhooks-trigger-auto` pipeline will automatically get triggered.

Then if you come back into the webhook settings, you will see the message `Last delivery was successful.` meaning that GitHub successfully sent an `HTTP POST` request to my Jenkins webhook URL of `http://67.205.164.34:8080/github-webhook/`.

# Lab: Getting Started with App Engine

## Objectives

In this lab, you learn how to perform the following tasks:

 - Initialize App Engine.

 - Preview an App Engine application running locally in Cloud Shell.

 - Deploy an App Engine application, so that others can reach it.

 - Disable an App Engine application, when you no longer want it to be visible.


## Start Lab

 - Click Open Google Console.

 - Click Use another account and copy/paste credentials for this lab into the prompts.

 - Accept the terms and skip the recovery resource page.


### Activate Google Cloud Shell

 - In GCP console, on the top right toolbar, click the Open Cloud Shell button.

 - Cloud Shell icon

 - Click Continue. 


### Cloud Shell Terminal

You can list the active account name with this command:

 `gcloud auth list`

Output:

Credentialed accounts:
 - google1623327_student@qwiklabs.net
You can list the project ID with this command:

 `gcloud config list project`

Output:

[core]
project = qwiklabs-gcp-44776a13dea667a6
Full documentation of gcloud is available on Google Cloud gcloud Overview .

### Steps:

1. Initialize App Engine

 - Initialize your App Engine app with your project and choose its region:

    `gcloud app create --project=$DEVSHELL_PROJECT_ID`

 - When prompted, select the region where you want your App Engine application located.

 - Clone the source code repository for a sample application in the hello_world directory:

    `git clone https://github.com/GoogleCloudPlatform/python-docs-samples`

- Navigate to the source directory:

    `cd python-docs-samples/appengine/standard_python3/hello_world`

2. Run Hello World application locally

 - Execute the following command to download and update the packages list.

    `sudo apt-get update`

 - Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.

    `sudo apt-get install virtualenv`

 - If prompted [Y/n], press Y and then Enter.
    `virtualenv -p python3 venv`

 - Activate the virtual environment.

    `source venv/bin/activate`

 - Navigate to your project directory and install dependencies.

    `pip install  -r requirements.txt`

 - Run the application:

    `python main.py`

 - End the test, return to Cloud Shell and press Ctrl+C to abort the deployed service.

 - Using the Cloud Console, verify that the app is not deployed. In the Cloud Console, on the Navigation menu (Navigation menu), click App Engine > Dashboard.


3. Deploy and run Hello World on App Engine

 - To deploy your application to the App Engine Standard environment:

 - Navigate to the source directory:

    `cd ~/python-docs-samples/appengine/standard_python3/hello_world`

 - Deploy your Hello World application.

    `gcloud app deploy`

 - If prompted "Do you want to continue (Y/n)?", press Y and then Enter.

    `gcloud app browse`

 - Copy and paste the URL into a new browser window.


4. Disable the application

 - In the Cloud Console, on the Navigation menu (Navigation menu), click App Engine > Settings.

 - Click Disable application.

 - Read the dialog message. Enter the App ID and click DISABLE.

## End Lab

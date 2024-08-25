### Objectives
In this lab, you learn how to perform the following tasks:

Create a cloud-based application development environment by using Cloud Workstations.
Explore various Google services that you can use to deploy an app by asking Gemini context-based questions.
Prompt Gemini to provide templates that you can use to develop a basic app in Cloud Run.
Create, explore, and modify the app by using Gemini to explain and generate the code.
Run and test the app locally, and then deploy it to Google Cloud by using Gemini to generate the steps.

Full documentation of gcloud is available in the [gcloud CLI overview guide.](https://cloud.google.com/sdk/gcloud)

## Task 1. Configure your environment and account

1. Sign in to the Google Cloud console with your lab credentials, and open the Cloud Shell terminal window.
2. To set your project ID and region environment variables, in Cloud Shell, run the following commands:
   ```
     PROJECT_ID=$(gcloud config get-value project)
     REGION=us-east4
     echo "PROJECT_ID=${PROJECT_ID}"
     echo "REGION=${REGION}"
   ```
3. To store the signed-in Google user account in an environment variable, run the following command:
     ```
      USER=$(gcloud config get-value account 2> /dev/null)
      echo "USER=${USER}"
     ```
4. Enable the Cloud AI Companion API for Gemini:
   ```
    gcloud services enable cloudaicompanion.googleapis.com --project ${PROJECT_ID}
   ```
5. To use Gemini, grant the necessary IAM roles to your Google Cloud Qwiklabs user account:
   ```
    gcloud projects add-iam-policy-binding ${PROJECT_ID} --member user:${USER} --role=roles/cloudaicompanion.user
    gcloud projects add-iam-policy-binding ${PROJECT_ID} --member user:${USER} --role=roles/serviceusage.serviceUsageViewer
   ```
Adding these roles lets the user use Gemini assistance.

## Task 2. Create a Cloud Workstation
This lab uses Gemini assistance to develop an app with the Cloud Code plugin for Cloud Workstations IDE. Cloud Workstations is a fully managed integrated development environment that includes native integration with Gemini.
In this task, you configure and provision your Cloud Workstation environment, and you enable the Cloud Code plugin for Gemini.

### View the workstation cluster
A workstation cluster named my-cluster has been pre-created for this lab. This cluster is used to configure and create a workstation.

1. In the Google Cloud console, select the Navigation menu (Navigation menu icon), and then select View All Products > Tools > Cloud Workstations.
2. In the Navigation pane, click Cluster management.
3. Check the Status of the cluster. If the status of the cluster is Reconciling or Updating, periodically refresh and wait until it becomes Ready before moving to the next step.

### Create a workstation configuration

Before creating a workstation, you must create a workstation configuration in Cloud Workstations.

1. In the Navigation pane, click Workstation configurations, and then click Create Workstation Configuration.

2. Specify the following values:
   
   ![image](https://github.com/user-attachments/assets/e5088a2b-8dab-4f5f-903a-e51edb3a2b71)

3. Click Create.

4. Click Refresh.

5. Check the Status of the configuration being created. If the status of the configuration is Reconciling or Updating, periodically refresh and wait until the status becomes Ready before moving to the next step.

### Create a workstation

1. In the Navigation pane, click Workstations, and then click Create Workstation.

2. Specify the following values:
   
   ![image](https://github.com/user-attachments/assets/a2f7cf20-8ae0-4cf5-8744-ff2c80f6fa9b)

3. Click Create.
   After the workstation is created, it is listed under My workstations with a status of Stopped.

4. To start the workstation, click Start.
   As the workstation starts up, the status changes to Starting. Wait for the status to change to Running which indicates that it is ready to be used. It might take several minutes for the workstation to fully start up.

### Launch the IDE

To function properly, some extensions need third-party cookies to be enabled in your browser.

1. To enable third-party cookies in Chrome, in the Chrome menu, click Settings.
2. In the search bar, type Third-party cookies.
3. Click the Third-party cookies setting, and select Allow third-party cookies
   
   To launch the Code OSS IDE on the workstation, from the Workstations page in the Google Cloud console, click Launch.
   The IDE opens in a separate browser tab.

   ![image](https://github.com/user-attachments/assets/8f06e72b-d704-4249-840f-0c0b20832df0)

   




























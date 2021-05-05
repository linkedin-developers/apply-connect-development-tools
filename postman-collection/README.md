# How to use Postman Collections

The easiest way to get started using the Apply Connect APIs is to use our Postman collections. Postman is a free-to-download tool for making HTTP requests. You can find more details about Postman [here](https://www.postman.com).
The following steps outline the necessary actions in order to install Postman and gain certainty that everything is working as it should be.
If you prefer, you can explore our API with other tools like curl.

---
**IMPORTANT**

PLEASE NOTE THAT POSTMAN IS AN INDEPENDENT ENTITY AND IS NOT AFFILIATED WITH LINKEDIN. LINKEDIN IS PROVIDING THE FOLLOWING RESOURCES TO SUPPORT YOUR USE OF THE POSTMAN SERVICES BUT ULTIMATELY, ANY USE OF THIRD PARTY SERVICES, SUCH AS THE POSTMAN SERVICES, IS AT YOUR OWN DISCRETION AND RISK. LINKEDIN DOES NOT ENDORSE OR VET THE POSTMAN SERVICES AND IS NOT RESPONSIBLE FOR ANY DAMAGE OR LOSS OF DATA RESULTING FROM YOUR USE OF THIRD PARTY SERVICES. NOTHING HEREIN SHALL RESTRICT LINKEDIN'S ABILITY TO ENFORCE ALL OF ITS RIGHTS UNDER ITS AGREEMENTS WITH YOU.

---

## Install Postman

Visit www.getpostman.com and download the version of Postman required for your platform and complete Postman installation.

## Import Postman Collection

* Open Postman
* Click `Import` button, click `Choose Files` button and locate the required collection json file to import. An import success message appears for each collection imported and then you can see the collection in `Collections` tab.
* After a collection is successfully imported into postman, Click `...` icon next to an imported collection and click on `Edit` button to setup variables.
* Please set the value for the variables and click on `Update` button.
* You have successfully setup and ready to make API calls.

## Apply Connect Postman Collection Variables

|Variable Name|Description|
|---|---|
|parent_app_client_id|Client id of Parent's Application. It will be used to get an access token and call `Provision Customer Application` APIs|
|parent_app_client_secret|Client secret of Parent's Application. It will be used to get an access token and call `Provision Customer Application` APIs|
|customer_app_client_id|Client id of Customer's Application. It will be used to get an access token and call `Sync Jobs` APIs, etc.|
|customer_app_client_secret|Client secret of Customer's Application. It will be used to get an access token and call `Sync Jobs` APIs, etc.|
|integration_context|The value for `integration_context` is obtained when a customer has requested the `Apply Connect` integration using the `ATS Integration Configuration Plugin`|
|customer_webhook_url|Webhook url that will be used to receive job applications. It will be used when configuring `jobApplicationCallbackUrl` using `Sync Jobs` APIs.|
|job_application_id| Application id received when a successful application is delivered to a `customer_webhook_url`, it will be used when updating `jobApplicationLifecycleActions` APIs.|

## How to use Apply Connect Collections

To make it easier for developer's we've leveraged using Postman [environment variables](https://learning.postman.com/docs/sending-requests/variables/) across the various APIs. Below are notes of how some of the associated APIs work.

* Customer Configuration

  * get an access Token - Parent Application: A `parent_app_access_token` will be created and set to be used for the various APIs under the Customer Configuration directory. The `parent_app_access_token` has been set as a Bearer token and will be used for requests requiring it.

* Create and Manage Jobs

  * Sync Jobs: We've provided a sample, basic payload for configuring Apply Connect jobs using the initial variables you've set for your collection. Upon a successful request the `simple_job_posting_id` will be set as a variable automatically and will be referenced for "Sync Jobs - Creation Task Status".

  * Sync Job - Creation Task Status: The `simple_job_posting_id` variable has been referenced from the previous request, sending a request will automatically use that variable to check the task status.

# Authentication

The Roambi API relies on an authorization header to authenticate requests using
the OAuth 2.0 protocol. The OAuth 2.0 protocol provides both developers and end
users with security and ease of use. Developers should never need to store an
Roambi user's username and password information on the API client; this authorization
method keeps users secure and limits developers' liability.

## Authentication workflow

Roambi API authentication uses the following workflow:

1. Developer registers and obtains a client key and a client secret from Roambi.
* The developer's application contacts Roambi and requests a particular scope of access to a specific users' account.
* The Roambi server displays an OAuth 2.0 dialog to an Roambi user, asking the user to grant the application access to the User's Roambi account and data.
* If the Roambi user approves, Roambi server will return a temporary authorization code to the developer's application.
* The application receives the authorization code and exchanges it for an access token and refresh token from Roambi server.
* The application receives the access token and calls the Roambi API on the behalf of the Roambi user.

The following diagram illustrates the server-side workflow:

![Authentication Workflow](/attachments/token/kwghsqvygsfh7bi/?name=server_side_flow_450x420.png "Authentication Workflow")


## Registering your application

Register your application with Roambi to obtain a client key (`client_id`) and
client secret.

To register your application with Roambi Business:

1. On the left pane of the Roambi Business Administration console, click the
**API Clients** tab:

  ![API Clients Administration](http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/apiclients_450x284.png)

  The Administration console displays the **API Clients**  tab:

  ![API Clients Administration](http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/apiclients1_450x182.png)

* Click the **Create a New API Client** button to go to the
registration screen for your new API client:

  ![New API Client](http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/api_createnewclient1_450x402.png)

* Type the **Name** and **Description** for your app, and as prompted, check the
box to indicate that you have read and agreed to the [Roambi API Terms of Use](http://help.roambi.com/roambi-business/en/Subsystems/index/content/api/org-apitermsandconditions.html).

  Once you accept the Terms of Service, the console enables a**Done** button.

* Click the **Done** button.

  Your application is now registered and displayed on the API Clients tab:

  !['Application List'](http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/apiclient3_450x322.png)

* Click the client entry to view the application details:

  !['Application Details'](http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/api_clientdetails_450x254.png)

  The **Consumer Key**  maps to the Client ID parameter and the **Consumer Secret**  maps to the Client Secret parameter. You will need these parameters later.

<p class="body">The Roambi API relies on an authorization header to authenticate requests using the OAuth 2.0 protocol. The OAuth 2.0 protocol provides both developers and end users with security and ease of use. Developers should never need to store an Roambi user's username and password information on the API client; this authorization method keeps users secure and limits developers' liability.</p>
<h2><em>Authentication workflow</em></h2>
<p class="body">Roambi API&nbsp;authentication uses the following workflow:</p>
<ol>
   <li value="1">Developer registers and obtains a client key and a client secret from Roambi.</li>
   <li value="2">The developer's application contacts Roambi and requests a particular scope of access to a specific users' account.</li>
   <li value="3">The Roambi server displays an OAuth 2.0 dialog to an Roambi user, asking the user to grant the application access to the User's Roambi account and data.</li>
   <li value="4">If the Roambi user approves, Roambi server will return a temporary authorization code to the developer's application.</li>
   <li value="5">The application receives the authorization code and exchanges it for an access token and refresh token from Roambi server.</li>
   <li value="6">The application receives the access token and calls the Roambi API on the behalf of the Roambi user.</li>
</ol>
<p class="body">The following diagram illustrates the server-side workflow:</p>
<p>&nbsp;<img src="/attachments/token/kwghsqvygsfh7bi/?name=server_side_flow_450x420.png" alt="server_side_flow_450x420.png" /></p>
<p>&nbsp;</p>
<h2><em>Registering your application</em></h2>
<p>&nbsp;Register your application with Roambi to obtain a client key (<var>client_id</var>) and client secret.</p>
<p class="body">To register your application with&nbsp;Roambi Business:</p>
<ol>
   <li value="1">
      <p class="body">On the left pane of the&nbsp;Roambi Business&nbsp;Administration&nbsp;console, click the&nbsp;<strong>API Clients</strong>&nbsp;tab:</p>
      <p class="body"><img src="http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/apiclients_450x284.png" alt="" /></p>
      <p class="body">The&nbsp;Administration&nbsp;console displays the&nbsp;<strong>API Clients</strong>&nbsp;tab:</p>
      <p class="body"><img src="http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/apiclients1_450x182.png" alt="" /></p>
   </li>
   <li value="2">
      <p class="body">Click the&nbsp;<strong>Create a New API&nbsp;Client</strong>&nbsp;button to go to the registration screen for your new API client:</p>
      <p class="body"><img src="http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/api_createnewclient1_450x402.png" alt="" /></p>
   </li>
   <li value="3">
      <p class="body">Type the&nbsp;<strong>Name&nbsp;</strong>and&nbsp;<strong>Description&nbsp;</strong>for your app, and as prompted, check the box to indicate that you have read and agreed to the <a href="http://help.roambi.com/roambi-business/en/Subsystems/index/content/api/org-apitermsandconditions.html">Roambi API Terms of Use</a>.</p>
      <p class="body">Once you accept the Terms of Service, the console enables a<strong>Done&nbsp;</strong>button.</p>
   </li>
   <li value="4">
      <p class="body">Click the&nbsp;<strong>Done&nbsp;</strong>button.</p>
      <p class="body">Your application is now registered and displayed on the API&nbsp;Clients tab:</p>
      <p class="body"><img src="http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/apiclient3_450x322.png" alt="" /></p>
   </li>
   <li value="5">
      <p class="body">Click the client entry to view the application details:</p>
      <p><img src="http://help.roambi.com/roambi-business/en/Subsystems/index/content/resources/images/api_clientdetails_450x254.png" alt="" /></p>
      <p class="body">The&nbsp;<strong>Consumer Key</strong>&nbsp;maps to the Client ID parameter and the&nbsp;<strong>Consumer Secret</strong>&nbsp;maps to the Client Secret parameter. You will need these parameters later.</p>
   </li>
</ol>
<a href="https://github.com/Roambi/Roambi-API/wiki#quick-navigation"><em>Back to Quick Navigation</em></a> 
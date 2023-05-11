+++
title = "Enterprise Connection"
chapter = false
weight = 10
pre = "<b>4.1 </b>"
+++

Enterprise Connections in Auth0 allows external users to authenticate with Identity Providers (IdP) such as Okta, Google Workspace, and more.

### 1. Get Okta Integration Information

For this lab, we are providing sample organizations running on the Okta service. In order to create your organization, visit https://okta-cic-workshop-org-creator.herokuapp.com/. Here you will need to provide some information:

- **Auth0 Tenant Name**: This is the name of your own Auth0 tenant you are using at the moment. You can also find the name by going to https://manage.auth0.com/dashboard/region/tenant-name
- **A name for your organization**: Use the naming scheme your-name-workshop or similar unique names to avoid conflict with other lab participants
- **Email address**: You can use any email address, though we recommend using an @example.com email, e.g. your-name@example.com.
- **First and last name are optional** and can be entered if you want to see that this information will be transferred to Auth0 later on as well

Once you have entered your detail, you should receive a password for your user as well as a client ID that you can use to set up the SSO connection. Please note both as we will need it throughout the lab to login into Okta.

### 2. Create Enterprise Connection
In order to let the newly created organization sign into our application, you have to register it as a new OpenID Connect (OIDC) enterprise connection.

1. Go to **Authentication** --> **Enterprise** --> **Open ID connect** in the Auth0 Dashboard and click **create connection**.
2. Enter a connection name (this can be anything) and copy the Issuer URL and ClientID from the organization you just created.
3. Click on **Create** to complete the setup.

### 3. Test
- Log into your application again (by clicking the login button).
- When you enter your newly created user now (e.g. test@example.com), you should be redirected to your newly created organization and be able to sign in with the credentials that you received when registering the organization.
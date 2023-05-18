+++
title = "Enterprise Connection"
chapter = false
weight = 10
pre = "<b>4.1 </b>"
+++

Enterprise Connections in Auth0 allows external users to authenticate with Identity Providers (IdP) such as Okta, Google Workspace, and more.

We will configure Okta as an Enterprise Connection. You have 2 options in this workshop to get the configuration paramater:

1. Create a new Okta Tenant and the OIDC Application (free, no credit card required)
2. Use the Workshop Org Creator (might not work)

### 1. Create a new Okta Tenant and the OIDC Application (free, no credit card required)

The first step is to create a new Okta Tenant. If you already have one, you can also use it.

1. {{% button href="https://developer.okta.com/signup" %}}Click here to create your free Okta account{{% /button %}} No credit card is required.
2. You will receive an Email. Click on the link to activate your account.
3. Set the password of your Okta Account and you are ready to go.

Login to the Okta Admin Console. If you see the Okta Dashboard, click on the **Admin** button in top right corner.

1. In the navigation bar on the right, go to **Applications** -> **Applications**.
2. Click on **Create App Integration**
3. Select **OIDC - OpenID Connect** and **Web Application** click on **Next**.
4. Provide the following information
    - **App integration name**: `Auth0 IDP Login`
    - **Sign-in redirect URIs**: `https://<Auth0 Domain like in the chapter before>/login/callbackk`
    - Select **Allow everyone in your organization to access**
    - Click on **Save**
5. Copy the following values
    - **ClientID**
    - **Client Secret**: Click on **Edit**. At the section **CLIENT SECRETS**, copy the value of the generated secret.
    - **Okta Domain**: This is the domain of Okta Tenant. Copy it from the URL of the browser and remove **-admin** e.g. `my-domain.okta.com`

##### 2 Workshop Org Creater (might not work)

For this lab, we are providing sample organizations running on the Okta service. In order to create your organization, visit https://okta-cic-workshop-org-creator.herokuapp.com/. Here you will need to provide some information:

- **Auth0 Tenant Name**: This is the name of your own Auth0 tenant you are using at the moment. You can also find the name by going to https://manage.auth0.com/dashboard/region/tenant-name
- **A name for your organization**: Use the naming scheme your-name-workshop or similar unique names to avoid conflict with other lab participants
- **Email address**: You can use any email address, though we recommend using an @example.com email, e.g. your-name@example.com.
- **First and last name are optional** and can be entered if you want to see that this information will be transferred to Auth0 later on as well

Once you have entered your detail, you should receive a password for your user as well as a client ID that you can use to set up the SSO connection. Please note both as we will need it throughout the lab to login into Okta.

### 3. Create Enterprise Connection
In order to let the newly created organization sign into our application, you have to register it as a new OpenID Connect (OIDC) enterprise connection.

1. Go in the Auth0 Management Console to **Authentication** --> **Enterprise**
2. Click on the **+** of **Okta Workforce**
3. Enter the following
    - **Connection Name**: `Org1`
    - **Okta Domain**: The value you copied earlier e.g. my-domain.okta.com
    - **Client ID**: The value you copied earlier
    - **Client Secret**: The value you copied earlier
    - Click on **Create**
4. Switch to the tab **Login Experience**
5. Go to the section **Connection Button** and select **Display connection as a button**
6. Click on **Save**
7. Switch to the tab **Applications**
8. Enable for **CIC Workshop**

### 4. Test
1. Log into your application again (by clicking the login button). 
2. The button **Continue with <domain>.okta.com** shows up - click on it to sign-in.
3. You should be redirected to your newly created Enterprise Connection and be able to sign in with the credentials that you used to create your Okta Tenant or received when registering the organization.
4. Back at our Sample Application, you can get more details about the signed-in users in the top right corner.
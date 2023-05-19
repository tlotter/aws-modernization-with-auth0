+++
title = "Integrate Application"
chapter = false
weight = 30
pre = "<b>2. </b>"
+++
The sample application that we use in this Workshop uses Node.js. You are requested to evaluate Auth0 to provide the login and user management. In order to get started, make sure you have an Auth0 Tenant and cloned the sampled application as described in the previous chapter **Prerequisites**.

### 1. Login to Auth0 Management Console
- If you're using a CIC tenant from demo.okta, open the management console of your tenant via https://demo.okta
- If you're using a free trial tenant, sign in to https://manage.auth0.com

### 2. Create a new Application
1. Go to **Applications** -> **Applications** and click on **+ Create Application**.
2. Enter as Name `CIC Workshop`, select **Single Page Web Application** and click on **Create**.
3. On the prompted Quick Start menu, choose **JavaScript**.
    - Auth0 provides instructions on how to integrate with your existing App or download an example application. We use the sample application cloned from the previous step.
4. Switch to the tab **Settings**
    - Our server is running on http://localhost:3000, and the SDK will automatically register a new /callback route, so we can leave the default settings for callback URL (the URL a user is allowed to be redirected to after successful login) and logout URL.
    - Copy the values of **Domain** and the **Client ID**.

### 3. Integate Application

1. Open the file **auth_config.json**, which is in the root folder of the cloned sample application.
2. Paste the **Domain** and **Client ID** from the previous step.

Here is an example:
```
{
  "domain": "dev-piss2nvlxxxxxxxus.auth0.com",
  "clientId": "cgziiCcRAmxQzxX3RvxbgXXXXX"
}
```

### 3. Test
1. Save your project.
2. Start the application by typing `npm run dev ` into your terminal.
3. Navigate to `http://localhost:3000` and click on login.
4. You can now sign in with your Auth0 credentials, and a consent screen should appear that you can accept.

### 4. Next Step
- Congratulations, you now have a working login form!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to customize the login to resemble the Pizza0 brand and user journey better.
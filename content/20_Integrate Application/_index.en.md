+++
title = "Integrate Application"
chapter = false
weight = 30
pre = "<b>2. </b>"
+++
This sample B2B SaaS App (let's call it Pizza0) uses Node.js to host their services and they want to evaluate Auth0 to provide the login and user management. In order to get started, make sure you have an Auth0 Tenant and cloned the sampled application as described in **Prerequisites**.

### 1. Login to Auth0 Management Console
- If you're using a CIC tenant from demo.okta, open the management console of your tenant via https://demo.okta
- If you're using a free trial tenant, sign in to https://manage.auth0.com

### 2. Create and integrate a new Application
- Go to **Applications** and register a new **Single Page Web Application**. You can give it any name, for example `CIC Workshop`.
- On the prompted Quick Start menu, choose JavaScript and **I want to integrate with my app**.
- Follow the guidance on the screen to set up your integration.
- Code Integration Hint:
    - To specify the application client ID and domain, make a copy of **auth_config.json.example** and rename it to `auth_config.json`.
    - Then open it in a text editor and supply the values for your application: `{ "domain": "", "clientId": "" }`
- Configuration (Only applies if you're running this lab on your machine)
    - Our server is running on http://localhost:3000, and the SDK will automatically register a new /callback route, so we can leave the default settings for callback URL (the URL a user is allowed to be redirected to after successful login) and logout URL.

### 3. Test
1. Save your project.
2. Start it up by typing `npm run dev ` into your terminal.
3. Navigate to http://localhost:3000 and click on login.
4. You can now sign in with your Auth0 credentials, and a consent screen should appear that you can accept.

### 4. Next Step
- Congratulations, you now have a working login form!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to customize the login to resemble the Pizza0 brand and user journey better.
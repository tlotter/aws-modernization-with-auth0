+++
title = "Integrate Application"
chapter = false
weight = 30
pre = "<b>2. </b>"
+++
The sample application that we use in this Workshop uses Node.js. You are requested to evaluate Auth0 to provide the login and user management. In order to get started, make sure you have an Auth0 Tenant and cloned the sampled application as described in the previous chapter **Prerequisites**.

### 1. Login to Auth0 Management Console
- If you're using a free trial tenant, sign in to https://manage.auth0.com
- If you're using a CIC tenant from demo.okta, open the management console of your tenant via https://demo.okta

### 2. Create a new Application
1. Go to **Applications** -> **Applications** and click on **+ Create Application**.
2. Enter as Name `CIC Workshop`, select **Single Page Web Application** and click on **Create**.
3. On the prompted Quick Start menu, choose **JavaScript**.
    - Auth0 provides instructions on how to integrate with your existing App or download an example application. We use the sample application cloned from the previous step.
4. Switch to the tab **Settings** and enter as **Allowed Callback URLs**, **Allowed Logout URLs** and **Allowed Web Origins** the callback URL of your application `http://localhost:3000` (If you use Cloud9, the URL is different).
5. Click on **Save Changes**.

![Copy Domain and ClientID](images/20_10_callback_url.png)

### 3. Integrate Application

1. Switch to the folder **01-Login** in the cloned sample application.
2. Rename **auth_config.json.example** to **auth_config.json**
3. Open the file **auth_config.json**
4. Paste the **Domain** and **Client ID** from the **Settings**.
5. **Save** the file.

![Copy Domain and ClientID](images/20_20_Copy_Domain_ClientID.png)

### 3. Test
1. Save your project.
2. Change in the terminal to the folder **01-Login** `cd 01-Login`
3. Start the application by typing `npm run dev ` into your terminal.
4. Navigate to `http://localhost:3000` and click on login in the top right corner.
    - If an error the error "This site can’t be reached", did you save auth_configuration.json?
5. Click on **Sign up** to create a new user.
6. Accept the consent screen and you are successfully signed in.
7. Click in the top right corner on **Profile** to see the ID Token that the application gets from Auth0.

![Copy Domain and ClientID](images/20_30_user_profile_page.png)

### 4. Next Step
- Congratulations, you now have a working login form!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to customize the user journey.
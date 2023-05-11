+++
title = "Customize Login Form"
chapter = false
weight = 40
pre = "<b>3. </b>"
+++
We now have our simple login in place and users could sign into the Pizza0 application. It does look very generic though and lacks the official Pizza branding. Also, individual customers often use Social Sign-In to access the service which the service doesn't support at the moment as well. Let's change that!

### 1. Add Branding
1. In the Auth0 dashboard (https://manage.auth0.com), navigate to **Branding** -> **Universal Login** in the sidebar menu.
2. Enter the logo of Pizza0 as well as the primary and background color specified. You can find all this information in your project under **styleguide.md** or use
    - Pizza0 Logo: `https://pizza0lab.s3.eu-central-1.amazonaws.com/pizza.jpeg`
    - Pizza0 Primary color: `#EB5424`
    - Pizza0 Background color: `#3A3A3A`
3. Click on **Save**
4. Navigate to your application to retry your login.

### 2. Add Social Login
1. To enable a Social Login, navigate to **Authentication** -> **Social** in the sidebar menu. Google should already be listed as a provider.
2. To add another social provider, click on **Add** and choose one of the social providers presented. Preferably choose one that you have an account with to test the login afterwards e.g. LinkedIn or Facebook. Choose your preferred provider and follow the guidance to enable it.
3. Note: You don't have to enter a client ID and client secret right now as we are just testing this feature. In production deployments, we would always recommend setting your own client ID and client secret.
4. To activate your new social provider for the application, open the Social Providers menu, go to **Applications** and turn on the application you have registered before. When you now try to authenticate again you will be able to use your social provider to access the application.

### 3. Next Step
- Congratulations, you just made Pizza0 a lot more appealing!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to the next lab to make your platform fit for business customers and give them a great login experience!
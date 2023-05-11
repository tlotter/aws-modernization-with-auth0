+++
title = "Enable Collaboration"
chapter = false
weight = 70
pre = "<b>6. </b>"
+++

As a final step, we now want to bring in a second organization and make it collaborate with the first organization we have created. This way your customers can not only access their secure and isolated environment in your application, but can actually be invited to other environments as well.

### 1. Create additional Enterprise Connection and Auth0 Organization
First, we need a second organization with which we can try our collaboration scenario.

- Follow the steps specified in the chapter **Add Business Login**
    - Make sure to specify a different user and organization name.
    - Make sure that you also set metadata on the new organization, with the key `license` and the value `premium` (again all lowercase).
- Log in using your new application, and observe that you can still order small and medium pizzas, but the large pizza is now not available anymore due to your license.
    - Make sure that you sign in at least once with your new user into your application using your new organization!

Steps to complete:

1. Create a new Identity Provider on https://okta-saas-lab-org-creator.herokuapp.com and note down the returned information
2. Integrate the Identity Provider as an Enterprise Connection to Auth0 and activate it for the Pizza0 application
3. Create a new organization and activate the enterprise connection with auto-membership
4. Set your custom license metadata as `license` : `premium`

### 2. Enable Collaboration
To enable collaboration, we need to give our second organization (Org B) access to our first organization (Org A). 
1. navigate to Org A by selecting **Organizations** in the Auth0 sidebar and clicking on Org A.
2. Go to **Connections** and **Enable Connections** and select the newly created connection that Org B is based on.
3. Select **Disable Auto-Membership** and click on **Save**.
4. Next, go to **Members** in Org A and click on **Add Members**.
5. Type in the email address of your user from Org B and click on **Add Member(s)**.
6.  This setup just made sure that selected users from Org B can now log into Org A. But in order to do so, those users had to be invited first by an admin of Org A, making sure that not anyone from Org B can sign into Org A.

### 3. Test

1. Log in again into Org A, but now choose the connection created for Org B and the credentials of the second user you have created.
2. You should still be able to sign in, and you should be able to order the large pizza now as Org A has a corporate license which you can now leverage from your Org B.

#### 4. Congratulation
- Congratulations, you completed the basic use cases of the lab!
- In this short time, you were able to integrate a secure login into your application, customize its look and feel, onboard business customers, tailor your application to them and even make them collaborate and access each others environment.
- Hopefully, this provided you some good ideas about the capabilities of such features in a real-world application and for your own projects.
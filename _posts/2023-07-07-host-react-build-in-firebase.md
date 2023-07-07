---
layout: post
title:  "Host React Build in Firebase"
date:   2023-07-07
categories: Deployment
tags: [Deployment]
readtime: true
thumbnail-img: /assets/img/cloud-server-thumb.jpg
---
In this post, we will guide you through the process of hosting React Build in Firebase. Let's dive in and get started!

1. Set up a Firebase project:
    - Go to the Firebase Console (https://console.firebase.google.com/), sign in, and create a new project.
    - Follow the prompts to set up your project.


2. Install Firebase CLI:
    - Open your terminal or command prompt.
    - Run the following command to install the Firebase Command Line Interface (CLI) globally:
      ```shell
         npm install -g firebase-tools 
      ```


3. Build your React app:
    - In your React project folder, run the following command to create a production-ready build:
   ```shell
        npm run build
   ```
    - This will create an optimized build of your React app in the build folder.
4. Connect Firebase CLI with your project:
    - In your terminal or command prompt, navigate to your React project folder.
    - Run the following command to log in to Firebase and connect it to your project:
      ```shell
         firebase login
      ```
    - Follow the authentication process and log in with your Firebase account.
5. Initialize Firebase in your project:
    - Run the following command to initialize Firebase in your project folder:
       ```shell
         firebase init
      ```
    -  Select the Firebase features you want to set up. For hosting, choose "Hosting" using the arrow keys, and press Enter.
    -  Select your Firebase project from the list.
    -  When asked "What do you want to use as your public directory?", type "build" and press Enter.
    -  or Specify the build folder as your public directory.
    -  Choose "Yes" when asked to configure as a single-page app (SPA).
    -  When asked if you want to overwrite the `index.html file`, choose "No" (unless you want to replace it with the default Firebase configuration).
6. Deploy your React build to Firebase:
    - After initializing Firebase, you can deploy your React build by running the following command:
    ```shell
       firebase deploy
    ```
    -  The deployment process will start, and you'll see a Firebase Hosting URL once it's completed.
    -  Visit the provided URL to see your React app hosted on Firebase.

That's it! Your React app should now be successfully hosted on Firebase.

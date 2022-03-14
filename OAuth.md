# OAuth

## 1. What Is OAuth and Why to use?
OAuth (Open Authorization) is an open standard for access delegation, commonly used as a way for Internet users to grant websites or applications access to their information on other websites but without giving them the passwords. This mechanism is used by companies such as Amazon, Google, Facebook, Microsoft, and Twitter to permit users to share information about their accounts with third-party applications or websites. 
<hr/>

### Why OAuth?
![](https://i.imgur.com/DDhkZu0.png)

<hr/>

![](https://i.imgur.com/fjMi2qM.png)

<hr/>

## 2. OAuth and APIs, How OAuth Is Used to Access APIs?
Companies need to protect their REST APIs in a way that allows many devices to access them.

In the old days, you’d enter your username/password directory and the app would login directly as you. This gave rise to the delegated authorization problem.

“How can I allow an app to access my data without necessarily giving it my password?”

In the dialogs below, that’s what we’re talking about. This is an application asking if it can access data on your behalf.

![image](https://user-images.githubusercontent.com/52599778/158182916-10309a47-9c7b-4147-8527-d05075f65b57.png)


To break it down simply, OAuth is where:

1. App requests authorization from User
1. User authorizes App and delivers proof
1. App presents proof of authorization to server to get a Token
1. Token is restricted to only access what the User authorized for the specific App

<hr/>

## 3. OAuth 1.0 vs. OAuth 2.0
### OAuth 1.0
![](https://i.imgur.com/OzuNuVs.png)

<hr/>

### OAuth 2.0
![](https://i.imgur.com/H6Wvbmc.png)

[How to implement Google Authentication in Node JS using Passport JS](https://medium.com/@prashantramnyc/how-to-implement-google-authentication-in-node-js-using-passport-js-9873f244b55e)

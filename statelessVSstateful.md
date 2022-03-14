# Stateless vs stateful authentication :+1: 

## What is session based authentication (stateful) vs token based authentication (stateless)?
* stateful
Stateful authentication is way to identify user session by creating session on backend and generating session id it sent the session to client and its getting stored in session storage .
so whenever user makes any request with server locates a session on its side and check there is a session or by checking properties in session state finds the user information so thus user can get resource by server.

* stateless
In stateless Authentication in which session data get stored in client side. State get Signed with key using various methods such as JWT on server only have to verify that is take signature matches or not.Stateless authentication also called token bases authentication because of all state data is signed and encrypted so whenever user request anything from server it verify user token and response in behalf of that

## Draw flow diagrams to show the steps involved in each process
 Stateful
 1. The user sends a login request to the server.
2. The server authenticates the login request, sends a session to the database, and returns a cookie containing the session ID to the user.
3. The server checks in the database for the ID found in the cookie, if the ID is found it sends the requested pages to the user.
4. Now, the user sends new requests (with a cookie).
![](https://i.imgur.com/GwIVaBJ.png)


Stateless
1. The user sends a login request to the server.
2. The server authorizes the login and sends a token to the user.
3. The server checks the token is valid or not, if the token is valid it sends the requested pages to the user.
4. Now, the user sends a new request(with a token).
![](https://i.imgur.com/46tJvNq.png)


## What are the advantages and disadvantages of each?

### Stateful: 
**Advantages**
* Revoke the session anytime
* Easy to implement and manage for one-session-sever scenario
* Session data can be changed later (assume that for a one-session-sever, no inconsistent problem)

**Disadvantages**
* Increasing server overhead
* Fail to scale
* Difficult for 3rd party applications to use your credentials

### Stateless: 
**Advantages**
* Lower server overhead
* Easy to scale
* Good to integrate with 3rd party application

**Disadvantages**
* Cannot revoke the session anytime
* Relatively complex to implement for one-session-server scenario
* Session data cannot be changed until its expiration time

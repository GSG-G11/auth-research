# Session-management in Express

- What are sessions?
- What are the different ways of managing sessions in express?
- Create a minimal example of how to set up a session

# Session-management

## What are sessions?

- A web session is a series of contiguous actions by a visitor on an individual website within a given time frame. Any interaction that you have with a single website is recorded as a web session to that website property.

## Why are sessions important?

- Sessions can be analyzed in a way that reveals how users truly interact with an app.
- By combining analysis of session metadata (e.g., session length) with usage data (e.g., tracking certain in-app events) and then analyzing behavior across a user base, app businesses can identify opportunities or problems within their apps that can be optimized for improved performance down the line.

## How sessions works

- When the client makes a login request to the server, the server will create a session and store it on the server-side. When the server responds to the client, it sends a cookie. This cookie will contain the session’s unique id stored on the server, which will now be stored on the client. This cookie will be sent on every request to the server.
- We use this session ID and look up the session saved in the database or the session store to maintain a one-to-one match between a session and a cookie. This will make HTTP protocol connections stateful.

![](https://hazelcast.com/wp-content/uploads/2021/12/diagram-Web-Sessions.png)

## The difference between session and cookie:

- A cookie is a key-value pair that is stored in the browser. The browser attaches cookies to every HTTP request that is sent to the server.
- In a cookie, you can’t store a lot of data. A cookie cannot store any sort of user credentials or secret information. If we did that, a hacker could easily get hold of that information and steal personal data for malicious activities.
- On the other hand, the session data is stored on the server-side, i.e., a database or a session store. Hence, it can accommodate larger amounts of data. To access data from the server-side, a session is authenticated with a secret key or a session id that we get from the cookie on every request.

## Ways of managing sessions in express

If you just want to set up a "volatile" session, with no need to store/verify any information server side, you can use cookie based session. This is just an improvement for the user experience (remember choices, preferences...)
On the other hand, if you need to keep some record about that user (authentication, history...), you will need to use a server side session, and a database. Any client side data (like cookie) could be modified by the user.
Note that the last option is not less scalable, it depends on the storage method, MemoryStore by default in express-session package, according to the documentation. This package is powered by express team, so I guess it is robust enough for a production usage.

## Simple cookie-based session middleware.

A user session can be stored in two main ways with cookies: on the server or on the client. This module stores the session data on the client within a cookie, while a module like express-session stores only a session identifier on the client within a cookie and stores the session data on the server, typically in a database.

## Example of how to set up a session

To get you started, Run `npm init -y` in a directory and install the following libraries:

```
npm install express express-session
```

**Express-session**: an HTTP server-side framework used to create and manage a session middleware. This tutorial is all about sessions. Thus Express-session library will be the main focus.

Create an app.js file and write the following code:

```
const app = require('express')();
const session = require('express-session');

app.use(
  session({
    // It holds the secret key for session
    secret: 'shhh secret',
    // Forces the session to be saved
    // back to the session store
    resave: false,

    // Forces a session that is "uninitialized"
    // to be saved to the store
    saveUninitialized: true,
  })
);



const user = {
  name: 'Abedalrahman',
  age: 25,
};

app.get('/login', (req, res) => {
  // req.session.key = value

  req.session.user = user;

  //Sets the cookie to the client
  req.session.save();
  res.send('Logged in');
});

app.get('/user', (req, res) => {
  if (req.session.user) {
    res.send(req.session.user);
  } else {
    res.send('No user');
  }
});

app.get('/logout', (req, res) => {
  // Destroys the session
  req.session.destroy();
  res.send('logged out');
});

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});

```

- Login will set the session with user property.
- Logout will destroy the session properties.

By default, the sessions are stored in MemoryStore. This is not recommended for production use. Instead, it's advisable to use alternative session stores for production. We have multiple options to store the data, like:

- Databases like MySQL, MongoDB.
- Memory stores like Redis.
- ORM libraries like sequelize.

This was a basic example, and I hope it helped you understand the concept of session management in Node.js using Express.js and Express-session.

If you want to dig deeper, you can check the docs of [Express-session](https://www.npmjs.com/package/express-session)

Happy coding!!


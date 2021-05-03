# Front-End

## Getting Started

### Prerequisites
You'll need to have [`yarn`](https://classic.yarnpkg.com/en/) installed on your computer. Follow directions [here](https://classic.yarnpkg.com/en/docs/install) to get yarn set up.

Unless you have access to the ecs-utd-events organizations (i.e. you are a maintainer) you will likely have to fork the repo to your personal GitHub account. Once you've forked the repository you can then clone the repo to your local machine, make changes, commit them, push them back to the forked repo and then submit a Pull Request to the main repo.

If you are a maintainer then you can simply clone the original repository. You can do so by using the following command:

`git clone https://github.com/ecs-utd-events/ecs-utd-events.git`.

Once you have the repository on your local machine, navigate inside the ecs-utd-events and then into the front-end folder. Here you'll want to run:

`yarn install` or simply `yarn`

This will install all the dependencies in the React project.

### Environment Setup
Inside the front-end folder you'll need to create a `.env` file to hold environment variables necessary to connect the front-end with the back-end server and Firebase Authentication. We have created a default `.env` file for developers testing on their local machine that connects to a staging/development database. This way any changes to the data/users does not effect our live site.

Copy and paste the following into your `.env` file:
```
REACT_APP_SERVER_URL="https://ecsutdevents-dev.azurewebsites.net"
REACT_APP_FIREBASE_CONFIG_APIKEY="AIzaSyC3l1wm0HeN54hct_VKVIaRYagvIqXfuKo"
REACT_APP_FIREBASE_CONFIG_AUTHDOMAIN="ecs-utdevents-dev.firebaseapp.com",
REACT_APP_FIREBASE_CONFIG_PROJECTID="ecs-utdevents-dev",
REACT_APP_FIREBASE_CONFIG_STORAGEBUCKET="ecs-utdevents-dev.appspot.com",
REACT_APP_FIREBASE_CONFIG_MESSAGINGSENDERID="486765773237",
REACT_APP_FIREBASE_CONFIG_APPID="1:486765773237:web:b07f6b68a760c19d9359fc",
REACT_APP_FIREBASE_CONFIG_MEASUREMENTID="G-E79XC8FBLG"
```

### Run Locally
Now you can start running the front-end code base locally! Simply run:

`yarn start`

from inside the front-end/ folder and you should be led to a local version of the website.

## React Context
React Context is a relatively new feature that allows for certain data to be made available throughout all child components of the Context without having to pass it in as a property. This is especially useful when there may be many intermediate components that don't directly use the data but have children who do. There are two important instances where we use contexts: **User Context** and **AllOrgContext**.

You can read more about React Context and its uses [here](https://reactjs.org/docs/context.html).
### User Context
User Context is used to manage the information of a logged in organization throughout the application. In [UserProvider.jsx](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/providers/UserProvider.jsx) we create the UserContext and it's appropriate provider. Here we use Firebase's Authentication API to set our user and once we have received the user we fetch the corresponding organization data from our back-end Web API using the user's ID. 

We then create an object that stores both the Firebase Authentication data and the organization object and pass it into the UserContext.Provider as the value to be shared with all the children components. Now inside of any child component we can import `UserContext`, pass it into the `useContext()` React hook like so: `useContext(UserContext)` and get the org and user data.

### AllOrgContext
Similarly, we realized that Firebase charges us by the number of queries we make to the database and wanted to reduce the number of times we called for all the organization data. Since the organization data does not change frequently and we need to use it frequently to convert orgIDs to shortNames or to full names we created a AllOrgContext within [AllOrgProvider.jsx](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/providers/AllOrgProvider.jsx). Here we simply fetch all the organization data, store it in a state variable, and pass it in as the value for the `AllOrgContext.Provider`. Now we can access all the organization data anywhere in the application without having to refetch the data.

In the future we may want to use Contexts to create a light vs. dark theme and to reduce other frequent fetch requests (such as tags or events).

## Firebase Authentication

The Front-End directly connects to Firebase for Authentication. This is handled mainly in the following files:

* [**UserProvider.jsx**](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/providers/UserProvider.jsx): we explain this above in [UserContext](./#user-context).

* [**AdminTab.js**](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/components/AdminTab.js): here we must provide the function for an organization to logout.

* [**NavbarComponent.js**](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/components/NavbarComponent.js): same as above.

* [**Login.js**](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/pages/Login.js): here we handle submitting a given username and password to Firebase for login and then allowing the UserContext to propagate changes throughout the application.

* [**firebase.js**](https://github.com/ecs-utd-events/ecs-utd-events/blob/dev/front-end/src/firebase.js): this file simply takes in all the environment variables necessary and establishes a connection with Firebase. This is then imported in all the above files to allow access to the [Firebase Auth API](https://firebase.google.com/docs/auth/web/start?hl=en).

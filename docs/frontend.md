# Front-End

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

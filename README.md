# Br Dev Streamers

![Logo](/logo.svg)


## Services

This diagram shows an overview of the main components and services of the Br Dev Streamers application.

![Services](/brstreamers-services.png)


### Index Flow

This flow represents the user accessing the website through https://brstreamers.dev

Observe that in a first access the application goes to the Twitch API. The response is cached with a TTL of 60 seconds.

After that, any user that access (within the TTL) will get their values from the cache (Redis).
![Index Flow](/brstreamers-index.png)


### Authentication Flow

This flow represents the user authentication. When the user clicks on the Login button, they are redirected Auth0 -> Twitch. Then after the successful login a JWT Token is stored as a Cookie.
![Authentication Flow](/brstreamers-auth.png)


### User Flow

This flow represents the CRUD operations for the User entity. When the user does on of the CRUD operations, the React application sends the payload and the JWT Token to the API.
The API then retrieves the jks.json and checks the JWT signature. If it is successful the application then allows the operation to happen.
![User Flow](/brstreamers-user.png)
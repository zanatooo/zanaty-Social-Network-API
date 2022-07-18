# zanaty-Social-Network-API
MongoDB is a popular choice for many social networks due to its speed with large amounts of data and flexibility with unstructured data. 

I built an API for a social network web application where users can share their thoughts, react to friends’ thoughts, and create a friend list. I used Express.js for routing, a MongoDB database, and the Mongoose ODM. In addition to using the Express.js and Mongoose packages.

Because this application won’t be deployed, I created a walkthrough video that demonstrates its functionality and all of the following acceptance criteria being met. 

[WalkThrough Video 1](https://watch.screencastify.com/v/NvbG45Z8WtqD5YeWEcrw)

[Walkthrough Video 2](https://watch.screencastify.com/v/WzE3kuXRsyN5YuKiNcNF)


User Story

AS A social media startup
I WANT an API for my social network that uses a NoSQL database
SO THAT my website can handle large amounts of unstructured data

Acceptance Criteria
GIVEN a social network API
WHEN I enter the command to invoke the application
THEN my server is started and the Mongoose models are synced to the MongoDB database
WHEN I open API GET routes in Insomnia for users and thoughts
THEN the data for each of these routes is displayed in a formatted JSON
WHEN I test API POST, PUT, and DELETE routes in Insomnia
THEN I am able to successfully create, update, and delete users and thoughts in my database
WHEN I test API POST and DELETE routes in Insomnia
THEN I am able to successfully create and delete reactions to thoughts and add and remove friends to a user’s friend list

Mock-Up
[Get Users](./images/GetUser.png)
[Get User by ID](./images/GetUserbyID.png)
[Add Friends](./images/AddFriends.png)

Getting Started
Use the following guidelines to set up your models and API routes:

Models
User

username

String
Unique
Required
Trimmed
email

String
Required
Unique
Must match a valid email address (look into Mongoose's matching validation)
thoughts

Array of _id values referencing the Thought model
friends

Array of _id values referencing the User model (self-reference)
Schema Settings

Create a virtual called friendCount that retrieves the length of the user's friends array field on query.

Thought

thoughtText

String
Required
Must be between 1 and 280 characters
createdAt

Date
Set default value to the current timestamp
Use a getter method to format the timestamp on query
username (The user that created this thought)

String
Required
reactions (These are like replies)

Array of nested documents created with the reactionSchema
Schema Settings

Create a virtual called reactionCount that retrieves the length of the thought's reactions array field on query.

Reaction (SCHEMA ONLY)

reactionId

Use Mongoose's ObjectId data type
Default value is set to a new ObjectId
reactionBody

String
Required
280 character maximum
username

String
Required
createdAt

Date
Set default value to the current timestamp
Use a getter method to format the timestamp on query
Schema Settings

This will not be a model, but rather will be used as the reaction field's subdocument schema in the Thought model.

API Routes
/api/users

GET all users

GET a single user by its _id and populated thought and friend data

POST a new user:


Developer:
Mohammed Elzanaty
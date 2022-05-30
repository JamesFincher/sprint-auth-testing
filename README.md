Read these instructions carefully. Understand exactly what is expected before starting this Sprint Challenge.

This challenge allows you to practice the concepts and techniques learned over the past sprint and apply them in a concrete project. This sprint explored Authentication and Testing. During this sprint, you studied authentication, JSON web tokens, unit testing, and backend testing. In your challenge this week, you will demonstrate your mastery of these skills by creating a dad jokes app.

This is an individual assessment. All work must be your own. All projects will be submitted to Codegrade for automated review. You will also be given feedback by code reviewers on Monday following the challenge submission. For more information on the review process click here.

You are not allowed to collaborate during the sprint challenge.

Project Setup
Run npm install to install your dependencies.
Build your database executing npm run migrate.
Run tests locally executing npm test.
Project Instructions
Dad jokes are all the rage these days! In this challenge, you will build a real wise-guy application.

Users must be able to call the [POST] /api/auth/register endpoint to create a new account, and the [POST] /api/auth/login endpoint to get a token.

We also need to make sure nobody without the token can call [GET] /api/jokes and gain access to our dad jokes.

We will hash the user's password using bcryptjs, and use JSON Web Tokens and the jsonwebtoken library.

MVP
Your finished project must include all of the following requirements (further instructions are found inside each file):

An authentication workflow with functionality for account creation and login, implemented inside api/auth/auth-router.js.
Middleware used to restrict access to resources from non-authenticated requests, implemented inside api/middleware/restricted.js.
A minimum of 2 tests per API endpoint, written inside api/server.test.js.
IMPORTANT Notes:

Do not exceed 2^8 rounds of hashing with bcryptjs.
If you use environment variables make sure to provide fallbacks in the code (e.g. process.env.SECRET || "shh").
You are welcome to create additional files but do not move or rename existing files or folders.
Do not alter your package.json file except to install extra libraries. Do not update existing packages.
The database already has the users table, but if you run into issues, the migration is available.
In your solution, it is essential that you follow best practices and produce clean and professional results.
Schedule time to review, refine, and assess your work and perform basic professional polishing.
Submission format
Submit via Codegrade by pushing commits to your main branch on Github.
Check Codegrade before the deadline to compare its results against your local tests.
Check Codegrade on the days following the Sprint Challenge for reviewer feedback.
New commits will be evaluated by Codegrade if pushed before the sprint challenge deadline.
Interview Questions
Be prepared to demonstrate your understanding of this week's concepts by answering questions on the following topics.

Differences between using sessions or JSON Web Tokens for authentication.
With sessions, after a user successfully logs in, the server will generate a sessionId, signed with a secret key, and save that into the database. On the client side, it will send a cookie with that sessionId to the browser and the browser will save that cookie to local storage and include the cookie automatically with every subsequent request. JSON Web Tokens, on the other hand, are stateless, meaning they are never saved to the database. Instead, they are encrypted tokens that are signed (to ensure they do are not altered and are authentic) and include the user_id right inside the token- thus no database lookup is required to identify the user. API calls that require authentication must include an Authorization token in the header to go through.

What does bcryptjs do to help us store passwords in a secure manner?
Bcryptjs hashes our passwords, which means we never can actually see, store, or access the plain text password of a user. Instead we store the hash, which bcryptjs creates for us. For a given input (e.g. "password123") bcrypt will always produce the same output (e.g. "#39rFEECN3jjfklsr3u2jfnvz>R") but it's impossible (or mathematically infeasible) to "reverse engineer" the plaintext password from the hash. Bcryptjs also adds a random "salt" to the password the user enters and allows you to hash the password as many times as you'd like, making it harder even harder to reverse engineer for hackers.

How are unit tests different from integration and end-to-end testing?
Unit tests are designed to test specific pieces (i.e. units- usually these are functions) of your code in isolation. That way, anytime you're changing code, you can see if your code broke something. Unit tests also help document what a given function or class is expected to do. Integration tests, on the other hand, are designed to test the end user functionality, which usually involves many moving pieces. Both are useful, but for different purposes. End to end testing is more centered around the user, and can help specify how your application is expected to work and when it breaks and where. Unit tests are more granular and allow you to identify when a given function breaks. It's possible to have all your unit tests passing but your integration tests fail, because your functions are doing what you expect in isolation but your application is not accomplishing what you'd like it to for your users!

How does Test Driven Development change the way we write applications and tests?
Test Driven Development means before you write your functions/code, you write your tests first. You write your test, so you know precisely what you're expecting a given function to do, and then you write the function to fulfill the requirements of that test, and get the test passing. Once the test passing, you can refactor your code and keep running the test and as long as it's passing you know your refactor didn't break anything. I personally like writing test.todos in Jest as a happy medium between true Test Driven Development and starting with code- I list out each requirement as a test.todo, so I know what I'm trying to build, build my function and test it manually (using console.log() or httpie etc.) and then start setting up the specific tests I have descriptions for.

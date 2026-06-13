# Short Response Questions

Answer each question below in your own words. Aim for 3–5 sentences per answer. Be specific — use the exact terms and concepts from the lesson.

Your responses will each be evaluated out of 6 points. You can earn 3 points for writing quality and 3 points for the accuracy and precision of the technical content per question.

---

## Question 1: Express vs `node:http`

Express is described as a framework that "wraps" `node:http`. What does that mean? Compare how you would handle a `GET /api/users` request in `node:http` versus in Express. What does Express do for you automatically that you had to write manually with `node:http`?

**Your answer here**:

Saying express "wraps" `node:http` means it builds a cleaner, higher-level abstraction layer over the clunky native node features to make routing and requests easier to manage. in `node:http`, you have to manually parse the URL string, check `req.method === 'GET'`, manually set headers, and stringify JSON data using `res.end()`. express handles all of that boilerplates automatically with clean methods like `app.get('/api/users', ...)` and `res.json()`, saving you from writing repetitive parsing logic.

---

## Question 2: Endpoints, Controllers, and Middleware

What are **controllers** and **middleware** in Express? What are each responsible for and how do they work together to handle incoming requests?

**Your answer here**:

Middleware functions are intermediate steps in the request-response cycle that examine, modify, or protect incoming requests (like logging or authentication) before passing them along using the `next()` function. controllers are the final destination functions at the end of an endpoint route that actually fulfill the user's request and send back the final response. They work together as a pipeline where a request passes through various middleware checks first, and if everything passes, the controller handles the core logic and finishes the cycle.

## Question 3: Query Strings and Route Parameters

How are **query strings** and **route parameters** similar? How are they different? In your answer, provide an example of when you would use each.

**Your answer here**:
Both query strings and route parameters are tools used to pass dynamic data from the client's URL straight into your server-side code. route parameters are a required part of the URL path used to target a specific resource, like using `/api/users/:id` to fetch one exact user profile by their ID. query strings are optional key-value pairs appended to the end of a URL after a `?`, which are perfect for filtering, sorting, or searching through a collection, like `/api/users?status=active`.

---

## Question 4: Same-Origin Requests

For API fetch calls from a client-side application, explain the difference between fetching from endpoints with relative paths like `/api/quotes` and fetching from endpoints with a full URL like `https://dog.ceo/api/breeds/image/random`. Why do we not send a fetch using a url like `http://localhost:8080/api/quotes`?

**Your answer here**:
Fetching with a relative path like `/api/quotes` assumes a same-origin request, meaning the browser automatically appends the current domain and port you're already browsing on. fetching a full URL like `https://dog.ceo/...` is a cross-origin request that goes out to an entirely separate external server. We avoid hardcoding URLs like `http://localhost:8080/api/quotes` in front-end code because it completely breaks your application once you deploy it to a live production server where the backend is no longer running on your personal local machine.

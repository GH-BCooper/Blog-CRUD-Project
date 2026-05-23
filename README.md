// Module Imports
import express from "express";
import bodyParser from "body-parser";
import axios from "axios";


// Express App Configuration
const app = express();
const port = 3000;

const API_URL = "http://localhost:4000";


// Middleware Configuration
app.use(express.static("public"));

app.use(bodyParser.urlencoded({ extended: true }));

app.use(bodyParser.json());


// Home Route
app.get("/", async (req, res) => {

  try {

    // Fetching All Posts
    const response = await axios.get(`${API_URL}/posts`);

    console.log(response);


    // Rendering Homepage
    res.render("index.ejs", {
      posts: response.data
    });

  } catch (error) {

    // Error Handling
    res.status(500).json({
      message: "Error fetching posts"
    });

  }

});


// New Post Page Route
app.get("/new", (req, res) => {

  res.render("modify.ejs", {
    heading: "New Post",
    submit: "Create Post"
  });

});


// Edit Post Page Route
app.get("/edit/:id", async (req, res) => {

  try {

    // Fetching Single Post
    const response = await axios.get(
      `${API_URL}/posts/${req.params.id}`
    );

    console.log(response.data);


    // Rendering Edit Page
    res.render("modify.ejs", {
      heading: "Edit Post",
      submit: "Update Post",
      post: response.data,
    });

  } catch (error) {

    // Error Handling
    res.status(500).json({
      message: "Error fetching post"
    });

  }

});


// Create Post Route
app.post("/api/posts", async (req, res) => {

  try {

    // Sending Post Request
    const response = await axios.post(
      `${API_URL}/posts`,
      req.body
    );

    console.log(response.data);

    res.redirect("/");

  } catch (error) {

    // Error Handling
    res.status(500).json({
      message: "Error creating post"
    });

  }

});


// Update Post Route
app.post("/api/posts/:id", async (req, res) => {

  console.log("called");

  try {

    // Sending Patch Request
    const response = await axios.patch(
      `${API_URL}/posts/${req.params.id}`,
      req.body
    );

    console.log(response.data);

    res.redirect("/");

  } catch (error) {

    // Error Handling
    res.status(500).json({
      message: "Error updating post"
    });

  }

});


// Delete Post Route
app.get("/api/posts/delete/:id", async (req, res) => {

  try {

    // Sending Delete Request
    await axios.delete(
      `${API_URL}/posts/${req.params.id}`
    );

    res.redirect("/");

  } catch (error) {

    // Error Handling
    res.status(500).json({
      message: "Error deleting post"
    });

  }

});


// Server Listener
app.listen(port, () => {

  console.log(
    `Backend server is running on http://localhost:${port}`
  );

});




⚙️ Application Architecture

The project consists of two servers:

1. Backend API Server

Runs on:

http://localhost:4000

Responsible for:

Managing blog data
Handling CRUD operations
Serving API endpoints
2. Frontend Server

Runs on:

http://localhost:3000

Responsible for:

Rendering EJS pages
Sending requests to the API server
Displaying blog posts dynamically
🔥 CRUD Functionalities
Create Post

Users can create a new blog post using a form.

Route
POST /api/posts
Read All Posts

Fetches and displays all blog posts.

Route
GET /posts
Read Single Post

Fetches a specific post using its ID.

Route
GET /posts/:id
Update Post

Updates selected fields of an existing post.

Route
PATCH /posts/:id
Delete Post

Deletes a blog post permanently.

Route
DELETE /posts/:id
⚙️ Core Concepts Used
Express.js Routing

Used for:

Page rendering
API endpoints
Dynamic route handling
Axios API Requests

Axios is used to:

Fetch posts
Create posts
Update posts
Delete posts

Example:

const response = await axios.get(`${API_URL}/posts`);
EJS Templating

Dynamic rendering is done using EJS:

<%= post.title %>
<%= post.content %>
Middleware Usage

Body Parser middleware handles:

JSON data
Form submissions
app.use(bodyParser.urlencoded({ extended: true }));





▶️ Installation & Setup
1. Clone the Repository
git clone YOUR_REPOSITORY_LINK
2. Navigate into the Project Folder
cd Blog-Management-App
3. Install Dependencies
npm install
4. Start the Backend API Server
node api.js
5. Start the Frontend Server

Open another terminal and run:

node index.js
🌍 Open in Browser





Visit:

http://localhost:3000
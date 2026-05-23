# 📝 Blog Management Web Application

A full-stack blog management application built using Node.js, Express.js, EJS, Axios, and REST APIs.  
The application allows users to create, edit, update, view, and delete blog posts dynamically.

---

# 🚀 Features

- Create new blog posts
- View all blog posts
- Edit existing blog posts
- Delete blog posts
- RESTful API integration
- Dynamic EJS templating
- In-memory database storage
- Responsive frontend rendering
- Error handling for API operations

---

# 🛠️ Technologies Used

- Node.js
- Express.js
- EJS
- Axios
- Body Parser
- HTML5
- CSS3

---

# 📁 Project Structure

```bash id="d7m2qx"
Blog-Management-App/
│
├── public/
│   └── styles/
│       └── main.css
│
├── views/
│   ├── index.ejs
│   └── modify.ejs
│
├── index.js
├── api.js
├── package.json
└── README.md




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
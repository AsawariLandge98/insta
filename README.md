index.js file
const express = require("express");
const app = express();
const path = require("path");
const port = 8080;

app.set("view engine", "ejs");  // Set EJS as the view engine
app.set("views", path.join(__dirname, "views"));  // Set the views directory

// Home route
app.get("/", (req, res) => {
    res.render("home", { username: "" });  // Render home.ejs (no username)
});

// Dynamic route for Instagram user page
app.get("/ig/:username", (req, res) => {
    const { username } = req.params;  // Capture username from the URL
    res.render("instagram", { username });  // Pass the username to the instagram.ejs template
});

// Start the server
app.listen(port, () => {
    console.log(`Server is listening on port ${port}`);
});

instagram.ejs file

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram</title>
</head>
<body>
    <h2>This page belongs to <%= username %> </h2>
    <button>follow</button>
    <button>Message</button>
</body>
</html>

---
title: Lesson 10 - Web Development (HTML, CSS, PHP)
subject: AL ICT
unit: 10
competency: Develops websites incorporating multi-media technologies (using HTML 5)
tags:
  - AL-ICT
  - Lesson-10
  - HTML5
  - CSS3
  - PHP
  - WebDevelopment
  - Flashcards
---
# :LiBook: Lesson 10: Web Development (HTML, CSS, PHP)

> [!ABSTRACT] Syllabus Scope (Competency 10)
> - 10.1 Need for web (WWW, Types of websites)
> - 10.2 User requirements and multimedia contents (Objectives, layouts, navigation)
> - 10.3 HTML tags for single web page design
> - 10.4 HTML for linked web pages (Hyperlinks, Lists, Tables, Media)
> - 10.5 CSS for changing appearance (Selectors, Formatting)
> - 10.6 Web authoring tools
> - 10.7 Dynamic web pages using PHP and MySQL (Forms, Database)
> - 10.8 Publishing and maintaining websites

---
## 10.1 Explores the need for web
- **The World Wide Web (WWW)**: An information system where documents and other web resources are identified by URLs, interconnected by hypertext links, and accessible via the Internet.
- **Types of Web Sites**: 
  - Information/News
  - Personal
  - Educational
  - Commercial / E-Commerce
  - Research
  - Web portals (gateways to information)
- **Web Structure**: Web content should have a systematic arrangement and logical structure.

## 10.2 Analyses user requirements (multimedia contents)
- **Defining Objectives**: A website must have clearly defined goals and target audiences.
- **Contents**: Determine what text, images, and media need to be displayed.
- **Information Layout**: Create an effective and appropriate visual arrangement.
- **Web Pages & Navigation**: Identify necessary web pages and map out a navigation structure to link them logically.

---
## 10.3 HTML Tags to Design a Single Web Page
HTML (Hypertext Markup Language) is the standard markup language for creating web pages.

### Building blocks of a web page
```html
<!DOCTYPE html>
<html> <!-- Page definition -->
<head> <!-- Head section -->
    <title>Page Title</title>
</head>
<body bgcolor="#FFFFFF"> <!-- Body section with background color -->
    
    <!-- Adding comments: This is an HTML comment -->
    
    <h1>Main Heading (h1 to h6)</h1>
    <p>This is a paragraph.</p>
    <br> <!-- Line break -->
    
    <p>
        <b>Bold Text</b>, <i>Italic Text</i>, <u>Underline Text</u>
    </p>

    <!-- Font tag (Legacy, but in syllabus) -->
    <font size="4" color="red">This text is red and sized 4.</font>
    
</body>
</html>
```

---
## 10.4 HTML to Create Linked Web Pages
A website consists of a **Home page** and **Linked pages**.

### Hyperlinks
```html
<!-- Different sections of the same page (bookmark) -->
<a href="#section1">Go to Section 1</a>
<div id="section1">Section 1 Content</div>

<!-- Different pages of the same site (local link) -->
<a href="about.html">About Us</a>

<!-- Pages of different sites (External link) -->
<a href="https://nie.lk">NIE Website</a>
```

### Lists
```html
<!-- Ordered List (Numbered) -->
<ol>
    <li>First Item</li>
    <li>Second Item</li>
</ol>

<!-- Unordered List (Bulleted) -->
<ul>
    <li>Apple</li>
    <li>Orange</li>
</ul>

<!-- Definition List -->
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
</dl>
```

### Tables and Media
```html
<!-- Image -->
<img src="image.jpg" alt="Description">

<!-- Table with merging -->
<table border="1">
    <caption>Student List</caption>
    <tr>
        <th>ID</th>
        <th>Name</th>
    </tr>
    <tr>
        <!-- Merging rows or columns uses rowspan and colspan -->
        <td colspan="2">No students yet</td>
    </tr>
</table>

<!-- Multimedia Objects -->
<audio controls><source src="audio.mp3"></audio>
<video controls><source src="video.mp4"></video>
```

---
## 10.5 CSS to Change the Appearance of Web Pages
CSS (Cascading Style Sheets) describes how HTML elements are displayed.

### Ways of Inserting CSS
1. **Inline**: `<p style="color:red;">Text</p>`
2. **Internal**: `<style> ... </style>` inside the `<head>`
3. **External**: `<link rel="stylesheet" href="style.css">`

### CSS Syntax & Comments
```css
/* This is a CSS comment */
selector { 
    property: value; 
}
```

### CSS Selectors
- **Element Selector**: `p { color: blue; }`
- **ID Selector**: `#header { font-size: 20px; }`
- **Class Selector**: `.highlight { background-color: yellow; }`
- **Group Selector**: `h1, h2, p { text-align: center; }`

### Appearance Formatting
- **Background**: `background-color`, `background-image`
- **Text & Fonts**: `color`, `font-family`, `font-size`, `text-align`
- **CSS can also style Links, Lists, and Tables to improve visual presentation.**

---
## 10.6 Web Authoring Tools
Software used to create web pages visually or through code (e.g., VS Code, Adobe Dreamweaver, Notepad++). They provide features like syntax highlighting, auto-completion, and live previews.

---
## 10.7 Dynamic Web Pages using PHP and MySQL
**Static** websites show the same content to all users. **Dynamic** websites change content based on user interaction or database records.

### Forms & Input Elements
```html
<form action="process.php" method="POST">
    <!-- Grouping form data -->
    <fieldset>
        <legend>User Login</legend>
        
        Username: <input type="text" name="uname" value=""><br>
        Password: <input type="password" name="pwd"><br>
        
        Gender: 
        <input type="radio" name="gender" value="M"> Male
        <input type="radio" name="gender" value="F"> Female <br>
        
        <input type="checkbox" name="agree"> I agree <br>
        
        Country:
        <select name="country">
            <option value="LK">Sri Lanka</option>
        </select><br>

        <input type="submit" value="Login">
        <input type="reset" value="Clear">
    </fieldset>
</form>
```
- **Attributes**: `type`, `name`, `value`, `action` (target script), `method` (`GET` or `POST`).

### Embedding PHP & MySQL
PHP runs on the server. Basic concepts include Variables (`$var`), Arrays, Control Structures (`if/else`, `while`), and Functions.

```php
<?php
// Variables
$username = $_POST['uname']; 

// Database Connectivity (mysqli)
$conn = mysqli_connect("localhost", "root", "", "my_db");

// Creating data source and entering data (Insert)
$sql_insert = "INSERT INTO users (uname) VALUES ('$username')";
mysqli_query($conn, $sql_insert);

// Retrieving data (Select)
$sql_select = "SELECT * FROM users";
$result = mysqli_query($conn, $sql_select);
while($row = mysqli_fetch_assoc($result)) {
    echo "User: " . $row['uname'];
}
?>
```
> [!INFO] Deep Dive Note
> For more PHP variables, `$_GET` vs `$_POST`, and MySQLi database connectivity code examples, read: [[Subtopics/PHP & MySQL Server-Side Scripting|PHP & MySQL Server-Side Scripting Guide]].

---
## 10.8 Publishes and Maintains Web Sites
- **Local Publishing**: Testing the website on a local computer using software like XAMPP or directly in a browser.
- **Internet Publishing**: 
  - Connecting to a Web Service Provider (Web Hosting).
  - Publishing web pages on a web server (e.g., via FTP).
- **Performance Factors**: 
  - Server speed and bandwidth.
  - Image optimization and multimedia size.
  - Code efficiency and minimal HTTP requests.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the difference between HTML `GET` and `POST` form submission methods? :: `GET` appends form data to the URL (limited data, less secure); `POST` sends data inside the HTTP request body (secure, handles large data).

What are the 4 main CSS selectors mentioned in the AL ICT syllabus? :: Element selector, ID selector, Class selector, and Group selector.

What tag is used in HTML5 to embed an external CSS file? :: `<link rel="stylesheet" href="filename.css">`.

What is the HTML tag used to group related elements in a form? :: The `<fieldset>` tag, often used with `<legend>`.

What is the difference between a local link and an external link in HTML? :: A local link points to another page on the same website, while an external link points to a completely different website.
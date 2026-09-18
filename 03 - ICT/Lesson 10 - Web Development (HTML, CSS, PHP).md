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

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Client-Server Architecture & HTTP/HTTPS
> - HTML5 Structure, Form Controls, Tables & Multimedia
> - CSS3 Styling, Selectors & Box Model
> - Client-side vs Server-side Scripting
> - PHP Syntax, Form processing (`$_GET`, `$_POST`), MySQL database integration (`mysqli`)

---
## 1. Client-Server Architecture & Web Technologies

- **Web Client (Browser)**: Requests web pages via HTTP/HTTPS, renders HTML/CSS/JS.
- **Web Server**: Hosts website files and executes server-side scripts (e.g., Apache, Nginx).
- **URL Structure**: `http://www.example.com/index.html` (`Protocol` :// `Domain` / `Path`).

---

## 2. HTML5 Core Structure & Key Tags

```html
<!DOCTYPE html>
<html>
<head>
    <title>AL ICT Web Page</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Welcome to AL ICT</h1>
    <p>This is a paragraph with <a href="https://nie.lk">link</a>.</p>
    
    <!-- HTML Table -->
    <table border="1">
        <tr><th>ID</th><th>Name</th></tr>
        <tr><td>1</td><td>Kamal</td></tr>
    </table>

    <!-- HTML Form -->
    <form action="process.php" method="POST">
        Username: <input type="text" name="uname"><br>
        Password: <input type="password" name="pword"><br>
        <input type="submit" value="Login">
    </form>
</body>
</html>
```

---
## 3. CSS3 Styling & Box Model

- **CSS Selectors**:
  - Element: `p { color: blue; }`
  - Class: `.highlight { background-color: yellow; }`
  - ID: `#header { font-size: 20px; }`
- **CSS Box Model**:
  $$	Total Width = Content Width + 	Padding + Border + 	Margin$$

---
## 3.5 HTML Media & Hyperlinks

- `<img src="..." alt="...">` — embed images.
- `<audio controls><source src="..."></audio>` — embed audio.
- `<video controls width="..."><source src="..."></video>` — embed video.
- Hyperlinks: `<a href="url">Link Text</a>` (anchor tag); `href` = Hypertext Reference.

## 3.6 HTML Lists & Text Formatting

- **Ordered List**: `<ol><li>Item</li></ol>`
- **Unordered List**: `<ul><li>Item</li></ul>`
- **Text Formatting**: `<b>`, `<i>`, `<u>`, `<strong>`, `<em>`, `<br>`, `<hr>`

---

## 3.7 CSS Insertion Methods & Syntax

- **Inline**: `<p style="color:red;">`
- **Internal**: `<style> ... </style>` inside `<head>`
- **External**: `<link rel="stylesheet" href="style.css">` (preferred)
- **CSS Syntax**: `selector { property: value; }`

---

## 3.8 CSS Selectors & Appearance

| Selector | Example | Target |
|:---|:---|:---|
| Element | `p { ... }` | All `<p>` tags |
| Class | `.highlight { ... }` | Elements with `class="highlight"` |
| ID | `#header { ... }` | Element with `id="header"` |

- **Appearance formatting**: `color`, `font-family`, `font-size`, `text-align`, `background-color`.
- **CSS Spacing**: `padding` (inside border), `margin` (outside border), `border`.
- **CSS Backgrounds**: `background-color`, `background-image`, `background-repeat`.
- **CSS Measuring Units**: `px` (pixels), `%`, `em`, `rem`.

---

## 3.9 Types of Websites & URL Structure

- **Static**: Fixed content (HTML + CSS only).
- **Dynamic**: Content changes (PHP + database).
- Types: News, Educational, Business, Personal, Entertainment, Research.
- **URL Parts**: `Protocol://Domain/Path` (e.g., `https://example.com/page.html`)

---

## 3.10 Web Publishing & Performance

- **Local Publishing**: Save files locally (`.html` + `.css`) and open in browser.
- **Internet Publishing**: Upload to web server (hosting) via FTP or hosting panel.
- **Web Authoring Tools**: VS Code, Notepad++, Dreamweaver.
- **Performance Factors**: Image size, number of HTTP requests, server speed, caching.

---

## 4. Client-Side vs Server-Side Scripting

- **Client-Side (JavaScript)**: Runs inside browser; fast user validation and UI animation.
- **Server-Side (PHP)**: Executes on server before sending plain HTML to client; handles database queries and authentication.

> [!INFO] Deep Dive Note
> For PHP variables, `$_GET` vs `$_POST`, and MySQLi database connectivity code examples, read: [[Subtopics/PHP & MySQL Server-Side Scripting|PHP & MySQL Server-Side Scripting Guide]].

---

## 5. PHP Basics (Server-Side)
- **Syntax**: `<?php ... ?>`; variables start with `$`; case-sensitive.
- **Variables**: `$name = "Kamal";`
- **Data Types**: String, Integer, Float, Boolean, Array, Object, NULL.
- **Superglobal Variables**: `$_GET`, `$_POST`, `$_SERVER`, `$_SESSION`, `$_COOKIE`.
- **Form Handling**: `$_POST['uname']` reads input from HTML form `name="uname"`.
- **Comments**: `// single line`, `/* multi */`, `# single line`.
- **Built-in Functions**: `strlen()`, `strtoupper()`, `date()`, `isset()`, `empty()`.
- **Loops**: `for`, `while`, `foreach`.
- **Conditionals**: `if`, `else`, `elseif`, `switch`.
---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the difference between HTML `GET` and `POST` form submission methods? :: `GET` appends form data to the URL visible in the browser address bar (limited data, unsecure for passwords); `POST` sends data inside the HTTP request body (hidden from URL, secure, supports large data).
<!--SR:!2026-10-01,14,290-->

What are the 4 components of the CSS Box Model? :: 1. Content, 2. Padding, 3. Border, 4. Margin.

What tag is used in HTML5 to embed an external CSS file? :: `<link rel="stylesheet" href="filename.css">`.

What is the difference between Client-Side and Server-Side scripting? :: Client-side scripts (e.g., JavaScript) run in the user's browser; Server-side scripts (e.g., PHP) run on the web server to generate dynamic HTML content before responding to the browser.
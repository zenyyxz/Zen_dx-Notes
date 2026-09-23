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

### Key roles

- **User**: person interacting with site via computer / smartphone.
- **Developer**: writes HTML/CSS/PHP instructions for browser to render.
- **Web server**: computer storing site content, serves it over Internet.
- **Web browser**: software to request, view, interact (Chrome, Firefox, Edge, Safari, Opera).
- **Web request**: browser -> server message asking for a page/resource.
- **Web response**: server -> browser reply with content + HTML display instructions.
- **Network**: connected devices sharing data via cables / Wi-Fi (Hub, Switch, Router).
- **Search engine**: scans/stores web content, returns keyword results (Google, Bing).

### WWW

- **World Wide Web (WWW)**: system of linked pages + multimedia accessed via Internet.
- Created by **Tim Berners-Lee, 1989 at CERN**. **W3C** maintains web standards.
- Links are **hyperlinks / hypertext** — click a word to jump to related info.
- **URL = address of page**. Parts: `Protocol (https:) + Domain (whatis.techtarget.com) + Path (/glossaries)`.
- **Features**: open source, distributed, hypertext system, cross-platform, single interface via browser, dynamic/evolving.
- Test HTML on each browser — rendering differs.

### WWW vs Internet

| WWW | Internet |
| --- | --- |
| Originated 1989 (Berners-Lee) | Originated 1960s (ARPANET) |
| Service *on* the Internet | Global network of networks |
| Uses HTTP/HTTPS | Uses TCP/IP |
| Based on hypertext, browsers | Based on routers, ISPs, DNS |
| Pages written in HTML | Infrastructure carrying WWW, email, FTP |

### Contents of a webpage

Text (headings/paragraphs), images/graphics/animations, video/audio, hyperlinks, forms/buttons, nav menu/footer, tables/lists, icons, search bars, slideshows, chat widgets.

### Types of Web Sites

- Information/News — BBC, CNN
- Personal — WordPress blogs, Medium
- Educational — Khan Academy, Coursera
- Commercial / E-Commerce — Microsoft, Apple, Amazon, eBay
- Research — ResearchGate, PubMed
- Entertainment/Social — YouTube, Netflix, Facebook, Instagram
- Government — department sites
- Web portals — Yahoo, MSN (gateway to mail, news, search)

## 10.2 Analyses user requirements (multimedia contents)

- **Defining Objectives**: clearly defined goals + target audience. Ask: what to boost? business areas? existing site problems? need to inform/sell/serve?
- **Contents**: what text, images, media to display.
- **Information Layout**: effective visual arrangement.
- **Web Pages & Navigation**: list pages needed, map navigation structure logically. Identify home vs linked pages, contents per page.

---

## 10.3 HTML Tags to Design a Single Web Page

HTML (Hypertext Markup Language) is the standard markup language for creating web pages.

### Workflow

1. **Edit**: text editor (`Notepad, TextEdit, Gedit`) or code editor (`VS Code, Sublime, Atom, Notepad++`) — syntax highlight + autocomplete. Word processors (`MS Word`) are *not* for coding.
2. **Save** with `.html` extension (e.g. `example.html`).
3. **View**: open in web browser which renders the code.

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
    <hr> <!-- Horizontal rule -->

    <p>
        <b>Bold</b>, <i>Italic</i>, <u>Underline</u>
    </p>

    <!-- Font tag (Legacy, but in syllabus) -->
    <font size="4" color="red">This text is red and sized 4.</font>
</body>
</html>
```

### Text formatting tags

| Tag | Effect |
| --- | --- |
| `<b>`, `<strong>` | bold / important bold |
| `<i>`, `<em>` | italic / emphasized |
| `<u>`, `<ins>` | underline / inserted |
| `<s>`, `<strike>`, `<del>` | strikethrough / deleted |
| `<mark>` | highlighted |
| `<big>`, `<small>` | larger / smaller |
| `<sup>`, `<sub>` | superscript / subscript |
| `<pre>` | preformatted (keeps spaces/line breaks) |
| `<marquee>` | scrolling text (obsolete, exam still asks). Attrs: `direction/behavior/scrollamount/scrolldelay/loop/width/height` |
| `<center>` | center horizontally (deprecated in HTML5 -> use CSS `text-align:center`) |
| `<font size color>` | legacy size + color |
| `<h1>...<h6>` | headings, `h1` largest |
| `<p>` | paragraph |
| `<br>`, `<hr>` | line break / horizontal line |

> [!TIP] Comments
> `<!-- comment -->` ignored by browser. Use to annotate or temporarily disable code.

---

## 10.4 HTML to Create Linked Web Pages

A website consists of a **Home page** (starting point) and **Linked pages**.

### Hyperlinks

```html
<!-- Different sections of the same page (bookmark) -->
<a href="#section1">Go to Section 1</a>
<h2 id="section1">Section 1</h2>

<!-- Different pages of the same site (local link) -->
<a href="about.html">About Us</a>
<a href="contact.html">Contact</a>

<!-- Pages of different sites (External link) -->
<a href="https://nie.lk">NIE Website</a>

<!-- Useful attributes -->
<a href="https://example.com" title="Tooltip" target="_blank">Open in new tab</a>

<!-- Image as link / Button as link -->
<a href="https://google.com"><img src="bird.jpg" alt="Bird"></a>
<a href="https://google.com"><button>Click Me</button></a>
```

- `<a>` attrs: `href`, `title` (tooltip), `target="_blank/_self"`.
- Bookmark = `id` on target + `href="#id"`.
- **Absolute path**: from root (`C:\Users\...\cheems.jpg`, `/home/user/report.txt`).
- **Relative path**: from current file (`xyz.jpg`, `images\cheems.jpg`). Shorter, preferred for same site.
- Local links can point to local images/audio/video/PDFs (`D:\Downloads\bird.jpg`).

### Lists
```html
<!-- Ordered List (Numbered) -->
<ol type="1" start="1">
    <li>First Item</li>
    <li>Second Item</li>
</ol>

<!-- Unordered List (Bulleted) -->
<ul type="disc">
    <li>Apple</li>
    <li>Orange</li>
</ul>

<!-- Definition List -->
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
</dl>
```
- `ol type="1/A/a/I/i"`, `ul type="disc/circle/square/none"`.

### Tables and Media
```html
<!-- Image -->
<img src="image.jpg" alt="Description" width="300" height="200">

<!-- Table with merging -->
<table border="1" width="100%" cellpadding="5" cellspacing="0">
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
<audio controls autoplay loop><source src="audio.mp3"></audio>
<video width="320" height="240" controls><source src="video.mp4"></video>
<embed src="movie.swf">
```

---

## 10.5 CSS to Change the Appearance of Web Pages

CSS (Cascading Style Sheets) describes how HTML elements are displayed. HTML = structure, CSS = presentation.

### Ways of Inserting CSS
1. **Inline**: `<p style="color:red;">Text</p>` — highest priority, avoid for maintainability.
2. **Internal**: `<style> ... </style>` inside `<head>` — good for single page.
3. **External**: `<link rel="stylesheet" type="text/css" href="style.css">` in `<head>` — best for multi-page. Can also `@import url("styles/main.css");`.

Priority: `Inline > Internal = External (last declared wins) > Browser default`. `!important` overrides everything:
```css
p { color: red !important; }
```

### CSS Syntax & Comments
```css
/* This is a CSS comment */
selector { 
    property: value; 
}
```
Syntax only for internal/external, not inline.

### CSS Selectors
- **Element Selector**: `p { color: blue; }`
- **ID Selector**: `#header { font-size: 24px; }` — one unique element.
- **Class Selector**: `.highlight { background-color: yellow; }` — many elements.
- **Group Selector**: `h1, h2, p { text-align: center; }`
- **Universal**: `* { margin:0; padding:0; box-sizing:border-box; }`
- **Compound** (no spaces): `p.highlight`, `h1#title`, `.btn.primary`

### Appearance Formatting

**Fonts**: `font-style/weight/size/family/variant/line-height`
```css
p { font-family: Arial, Helvetica, sans-serif; font-size:18px; font-weight:bold; }
```

**Text**: `color/text-align/transform/indent/decoration/shadow`
```css
h2 { text-align:center; text-transform:uppercase; }
p { text-indent:2em; text-decoration: underline dotted red 2px; }
h2 { text-shadow: 2px 2px 5px rgba(0,0,0,0.5); }
```

**Links — LVHA order**:
```css
a:link { color:blue; } a:visited { color:purple; }
a:hover { color:red; text-decoration:underline; }
a:active { color:green; } a:focus { outline:2px solid orange; }
a { text-decoration:none; }
```

**Lists**:
```css
ol { list-style-type: upper-roman; } /* decimal, decimal-leading-zero, lower/upper-roman, lower/upper-alpha, disc/circle/square/none */
ul { list-style-position: inside; } /* inside | outside */
ul { list-style-image: url('bullet.png'); }
ul { list-style: square inside url('bullet.png'); }
ul, ol { list-style:none; padding:0; margin:0; }
```

**Backgrounds** (shorthand order: color image position/size repeat attachment origin):
```css
body {
  background-color:#f0f0f0; background-image:url('bg.jpg');
  background-position:center; background-size:cover;
  background-repeat:no-repeat; background-attachment:fixed;
}
```

**Spacing**: `letter-spacing:2px; word-spacing:10px; white-space:nowrap;`

**Box model**: content (innermost, `width/height`) -> `padding` -> `border` -> `margin` (outermost) + `border-radius` + `box-shadow`.
```css
div { width:200px; height:100px; padding:10px;
  border:2px solid black; margin:20px;
  border-radius:25px; box-shadow:2px 2px 5px rgba(0,0,0,0.5); }
```
Borders: `border-width/style(solid/dashed/dotted/double)/color`, per-side `border-top/right/bottom/left`, `border-image`.

**Tables**:
```css
table { width:100%; border-collapse:collapse; border-spacing:10px; }
table, th, td { border:1px solid black; }
th, td { height:50px; padding:10px; text-align:center; vertical-align:middle; }
caption { caption-side:bottom; }
```
`border-collapse: collapse` merges borders, `separate` keeps spacing.

**Validation & Units**
- Validate at `http://jigsaw.w3.org/css-validator` — catches bad selectors/props.
- Relative (responsive): `%, em, rem, vw, vh, vmin, vmax, ch, ex`. Absolute (fixed/print): `px, cm, mm, in, pt, pc`.

---
## 10.6 Web Authoring Tools

Software to create/design/publish web content without hand-writing all code. Provides visual/drag-drop that generates HTML/CSS/JS.

**Purpose**: simplify creation (no HTML needed for beginners), speed up with templates, reduce syntax errors, professional responsive/SEO/e-commerce results, collaboration/version control.

**Types + Examples**:
- WYSIWYG: Adobe Dreamweaver, BlueGriffon, Webflow, Google Web Designer
- Code editors: VS Code, Sublime Text, Atom, Notepad++
- CMS / template: WordPress (+builders), Wix, Squarespace, Shopify
- IDEs: Eclipse for Web, PhpStorm, NetBeans
- Multimedia: Adobe Animate, Unity WebGL; Mobile: Thunkable, Ionic; Debugging: Lighthouse, VS Debugger

---
## 10.7 Dynamic Web Pages using PHP and MySQL

**Static** (fixed HTML/CSS, same for all, fast, manual update — e.g. portfolio) vs **Dynamic** (PHP/Ruby/Python/Node + DB, changes per user, slower, auto update — e.g. e-commerce, social).

### How PHP works

1. Browser requests `page.php` -> server recognises `.php`.
2. Server sends file to **PHP interpreter** (installed on server).
3. PHP runs logic, talks to MySQL if needed, generates HTML.
4. Server returns HTML to browser, browser renders.
- **Client-side** (HTML/CSS/JS) runs on user CPU; **Server-side** (PHP) runs on server CPU.

Setup locally with **XAMPP / WAMP** (virtual server), then `http://localhost/file.php`.

### Forms & Input Elements
```html
<form action="process.php" method="POST" autocomplete="on">
    <!-- Grouping form data -->
    <fieldset>
        <legend>User Login</legend>
        <label for="uname">Username:</label>
        <input type="text" id="uname" name="uname" value="" placeholder="Enter name" required><br>
        Password: <input type="password" name="pwd"><br>
        Email: <input type="email" name="email"><br>
        Age: <input type="number" name="age" min="14" max="65"><br>

        Gender: 
        <input type="radio" name="gender" value="M"> Male
        <input type="radio" name="gender" value="F"> Female <br>

        <input type="checkbox" name="agree" value="yes"> I agree <br>

        Country:
        <select name="country">
            <option value="LK">Sri Lanka</option>
        </select><br>

        <input type="submit" value="Login">
        <input type="reset" value="Clear">
    </fieldset>
</form>
```
- `<form>` attrs: `action` (target script), `method` (`GET` or `POST`), `autocomplete`.
- `<input>` attrs: `type/name/value/placeholder/readonly/required/disabled/id`. `name` = key sent to server.
- Types: `text/password/email/number/radio/checkbox/submit/reset/button/file/hidden`.
- `GET` appends to URL (visible, limited) vs `POST` in body (secure, large). `$_GET`, `$_POST`, `$_REQUEST`, `$_SERVER["REQUEST_METHOD"]`.

### Embedding PHP & MySQL
PHP runs on the server. See deep dive for full syntax, control structures, functions, superglobals.

```php
<?php
// Variables
$username = $_POST['uname']; 

// Database Connectivity (mysqli procedural)
$conn = mysqli_connect("localhost", "root", "", "my_db");
if (!$conn) { die("Connection failed: " . mysqli_connect_error()); }

// Creating data source and entering data (Insert) - sanitise!
$username = mysqli_real_escape_string($conn, $username);
$sql_insert = "INSERT INTO users (uname) VALUES ('$username')";
mysqli_query($conn, $sql_insert);

// Retrieving data (Select)
$sql_select = "SELECT * FROM users";
$result = mysqli_query($conn, $sql_select);
if (mysqli_num_rows($result) > 0) {
    while($row = mysqli_fetch_assoc($result)) {
        echo "User: " . $row['uname'] . "<br>";
    }
}
mysqli_close($conn);
?>
```
> [!INFO] Deep Dive Note
> For PHP variables, operators, `if/switch/loops`, functions/scope, built-ins, `$_GET` vs `$_POST`, procedural vs OOP MySQLi, `real_escape_string`, and INSERT/SELECT/UPDATE/CREATE examples, read: [[Subtopics/PHP & MySQL Server-Side Scripting|PHP & MySQL Server-Side Scripting Guide]].

---
## 10.8 Publishes and Maintains Web Sites

**Hosting components**: website (pages) + web server (stores/delivers) + hosting provider (rents space) + domain (human address -> IP via DNS) + 24/7 power/net.

**Flow**: user enters domain -> DNS resolves to IP -> browser sends HTTP/HTTPS request -> server returns pages.

- **Local Publishing**: test on own computer (`XAMPP`, browser, `localhost`).
- **Internet Publishing**: 
  - Rent space from hosting provider (free vs paid).
  - Upload via FTP / control panel to web server.
- **Performance Factors**: 
  - Server speed and bandwidth.
  - Image optimization and multimedia size.
  - Code efficiency and minimal HTTP requests.
  - Background attachment, table layout weight, unoptimized CSS.
- Syllabus expects: publish locally, identify free hosting sites, publish via free host, list performance factors.

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is the difference between HTML `GET` and `POST` form submission methods? :: `GET` appends form data to the URL (limited data, less secure); `POST` sends data inside the HTTP request body (secure, handles large data).

What are the 4 main CSS selectors mentioned in the AL ICT syllabus? :: Element selector, ID selector, Class selector, and Group selector.

What tag is used in HTML5 to embed an external CSS file? :: `<link rel="stylesheet" href="filename.css">`.

What is the HTML tag used to group related elements in a form? :: The `<fieldset>` tag, often used with `<legend>`.

What is the difference between a local link and an external link in HTML? :: A local link points to another page on the same website, while an external link points to a completely different website.

Who created the WWW and when, and what body maintains standards? :: Tim Berners-Lee in 1989 at CERN; W3C maintains standards.

What is the difference between WWW and Internet? :: WWW is a hypertext service using HTTP on top of the Internet; Internet is the global network infrastructure using TCP/IP.

What are the three parts of a URL? :: Protocol, domain name, path.

What is the priority order of CSS sources? :: Inline > Internal = External (last wins) > browser default; `!important` overrides all.

What does the CSS box model consist of from inside out? :: Content -> padding -> border -> margin, plus border-radius/box-shadow.

What is the LVHA order for link pseudo-classes? :: `:link`, `:visited`, `:hover`, `:active` (plus `:focus`).

What is the difference between `border-collapse: collapse` and `separate`? :: Collapse merges adjacent borders into one; separate keeps them distinct with `border-spacing`.

Name two relative and two absolute CSS units. :: Relative: `em`, `rem`, `%`, `vw/vh`; Absolute: `px`, `pt`, `cm`, `in`.

Where is the W3C CSS validation service hosted? :: `http://jigsaw.w3.org/css-validator`.

What attributes control merging in HTML tables? :: `colspan` for columns and `rowspan` for rows.

How do you create a bookmark link to a section on the same page? :: Give target `id="section1"` and link with `<a href="#section1">`.

What is the difference between static and dynamic web pages? :: Static is pre-generated fixed HTML same for all; dynamic is generated by server-side script + DB per user interaction.

Outline the 4 steps of how PHP works. :: Browser requests .php -> server sends to PHP interpreter -> PHP executes + DB query -> returns generated HTML to browser.

What 4 credentials are needed for `mysqli_connect`? :: Servername/host (localhost), username (root), password (""), dbname.

What is the purpose of `mysqli_real_escape_string`? :: Escapes special characters to treat input as data and prevent SQL injection.

What is the difference between procedural and OOP MySQLi connection check/close? :: Procedural: `mysqli_connect()`, `if(!$conn)`, `mysqli_close($conn)`; OOP: `new mysqli()`, `if($conn->connect_error)`, `$conn->close()`.

---
title: PHP & MySQL Server-Side Scripting Guide
subject: AL ICT
subtopic: Web Development
tags:
  - AL-ICT
  - Subtopic
  - PHP
  - MySQL
  - WebDevelopment
---
# :LiComputer: Subtopic: PHP & MySQL Server-Side Scripting Guide

> [!ABSTRACT] Core Focus
> PHP syntax basics, processing `$_GET` and `$_POST` form data, establishing MySQL database connection via `mysqli`, and executing dynamic database queries.

---
## 1. PHP Basic Syntax & Variables

PHP code blocks are enclosed in `<?php ... ?>`. All variable names start with a `$` sign.

```php
<?php
$name = "Kamal";
$age = 18;
echo "Student Name: " . $name . ", Age: " . $age;
?>
```

---
## 2. Processing HTML Form Data (`$_POST` vs `$_GET`)

### HTML Form (`login.html`):
```html
<form action="login.php" method="POST">
    <input type="text" name="username" placeholder="Username" required>
    <input type="password" name="password" placeholder="Password" required>
    <button type="submit">Login</button>
</form>
```

### PHP Processor (`login.php`):
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $uname = $_POST['username'];
    $pword = $_POST['password'];
    
    echo "Processing login for user: " . htmlspecialchars($uname);
}
?>
```

---
## 3. MySQL Database Integration (`mysqli`)

```php
<?php
$servername = "localhost";
$db_user = "root";
$db_pass = "";
$dbname = "school_db";

// 1. Establish Connection
$conn = mysqli_connect($servername, $db_user, $db_pass, $dbname);

// Check Connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

// 2. Execute SQL SELECT Query
$sql = "SELECT StudentID, Name, Marks FROM Student WHERE Marks >= 75";
$result = mysqli_query($conn, $sql);

// 3. Process Result Set
if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo "ID: " . $row["StudentID"] . " - Name: " . $row["Name"] . " - Marks: " . $row["Marks"] . "<br>";
    }
} else {
    echo "No records found.";
}

// 4. Close Connection
mysqli_close($conn);
?>
```

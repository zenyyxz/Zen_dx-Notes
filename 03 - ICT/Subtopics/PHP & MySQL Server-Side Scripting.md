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
> PHP syntax basics, control structures, functions/scope, built-ins, processing `$_GET` and `$_POST` form data, establishing MySQL database connection via `mysqli` (procedural vs OOP), and executing dynamic database queries.

---

## 1. PHP Intro & How It Works

- PHP (ex-Personal Home Page, Rasmus Lerdorf 1994, PHP/FI 1995) is a **server-side scripting language** for web development. Versions 3.0 modular, 4.0 Zend Engine, 5.0 OOP, 7.0 speed, 8.0 JIT.
- **Static** = fixed HTML same for all (fast, manual). **Dynamic** = PHP + DB per user (interactive, slower, auto).
- Flow: browser requests `.php` -> server -> **PHP interpreter** -> runs logic + MySQL -> outputs HTML -> browser renders.
- **Client-side** (HTML/CSS) uses user CPU; **server-side** (PHP) uses server CPU.
- Uses: CMS (WordPress), e-commerce (Magento/WooCommerce), frameworks (Laravel/Symfony), Facebook APIs.
- Run locally via **XAMPP / WAMP**, open `http://localhost/file.php`.

## 2. PHP Basic Syntax, Variables & Comments

PHP code blocks are enclosed in `<?php ... ?>`, embedded in HTML.

```php
<?php
$name = "Kamal"; // variable starts with $
$age = 18;
echo "Student Name: " . $name . ", Age: " . $age; // . concatenates
?>
```

- Naming: start with `$` + letter/underscore, case-sensitive (`$Age` != `$age`).
- Comments: `// line`, `# line`, `/* block */`.
- `var_dump($x)` prints type + value for debugging.
- Data types: string, int, float, bool, array, NULL.
- Operators: arithmetic `+-*/%`, assignment `= += .=`, comparison `== != > <`, increment `++ --`, logical `&& || !`, string `.` concat, `.=` append.

## 3. Control Structures & Functions

```php
<?php
// if-elseif-else
$marks = 85;
if ($marks >= 75) { echo "A"; }
elseif ($marks >= 65) { echo "B"; }
else { echo "F"; }

// switch
switch ($grade) {
  case "A": echo "Excellent"; break;
  default: echo "Other";
}

// loops: for / while / do-while / foreach
for ($i=1; $i<=3; $i++) { echo $i; }
$arr = array(1,2,3);
foreach ($arr as $v) { echo $v; }

// user function with default + return
function greet($name = "Guest") { return "Hello, $name!"; }
echo greet(); echo greet("Alice");
?>
```

- **Scope**: local (inside func), global (outside, access via `global` or `$GLOBALS['x']`), static (retains value across calls via `static $c=0`).
- Ternary: `$g = ($s>=90) ? "A" : "F";` — avoid deep nesting.

## 4. Commonly Used Built-ins

```php
<?php
echo strlen("Hello"); // 5
echo str_replace("Hello","Hi","Hello world!"); // Hi world!
echo substr("Hello world!",6,5); // world
echo count(array(1,2,3)); // 3
sort($arr); rsort($arr); // asc/desc; asort/arsort (by value), ksort/krsort (by key)
echo abs(-4.2); echo round(3.6); echo rand(1,10); echo sqrt(16);
if (isset($v)) { echo "set and not NULL"; }
if (empty($v)) { echo "empty"; }
print_r($arr); die("stop"); // exit()
echo implode(", ", ['a','b']); // a, b
print_r(explode(", ", "a, b, c"));
$safe = mysqli_real_escape_string($conn, $_POST['uname']);
?>
```

---

## 5. Processing HTML Form Data (`$_POST` vs `$_GET`)

Benefits of forms: access control (no direct DB), validation/sanitise, consistent entry, error feedback, controlled flow.

### HTML Form (`login.html`):
```html
<form action="login.php" method="POST" autocomplete="on">
    <label for="user">Username:</label>
    <input type="text" id="user" name="username" placeholder="Username" required>
    <input type="password" name="password" placeholder="Password" required>
    <input type="email" name="email" placeholder="mail@example.com">
    <input type="number" name="age" min="14" max="65">
    Gender: <input type="radio" name="gender" value="M">Male
            <input type="radio" name="gender" value="F">Female
    <input type="checkbox" name="agree" value="yes"> I agree
    <button type="submit">Login</button>
</form>
```
- `<form>` attrs: `action` (URL), `method` (`get/post`), `autocomplete`.
- `<input>` attrs: `type/name/value/placeholder/readonly/required/disabled/id`. `name` = key sent as `key=value`.
- `<label for="id">` focuses input on click. Group with `<fieldset><legend>`.
- Types: `text/password/email/number/radio/checkbox/select/submit/reset/button/file/hidden`.
- `GET` -> URL visible/limited; `POST` -> body secure/large.

### PHP Processor (`login.php`):
```php
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $uname = $_POST['username'];
    $pword = $_POST['password'];
    
    echo "Processing login for user: " . htmlspecialchars($uname);
}
// $_GET['x'], $_REQUEST['x'], $_SERVER, $GLOBALS also available
?>
```

---

## 6. MySQL Database Integration (`mysqli`)

PDO and MySQLi are PHP DB extensions; syllabus uses **MySQLi**. Need 4 credentials: host (`localhost`), user (`root`), pass (`""`), dbname.

| | Procedural | OOP |
|---|---|---|
| Connect | `mysqli_connect($s,$u,$p,$db)` | `new mysqli($s,$u,$p,$db)` |
| Check | `if (!$conn) die(mysqli_connect_error())` | `if ($conn->connect_error) die($conn->connect_error)` |
| Query | `mysqli_query($conn,$sql)` | `$conn->query($sql)` |
| Rows | `mysqli_num_rows($result)` | `$result->num_rows` |
| Fetch | `mysqli_fetch_assoc($result)` | `$result->fetch_assoc()` |
| Close | `mysqli_close($conn)` | `$conn->close()` |

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

// 2a. INSERT with sanitising (prevent SQL injection)
$uname = mysqli_real_escape_string($conn, $_POST['uname']);
$sql = "INSERT INTO users (username) VALUES ('$uname')";
mysqli_query($conn, $sql);

// 2b. Execute SQL SELECT Query
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

// 2c. Other queries: CREATE / UPDATE / ALTER
// $sql = "CREATE TABLE employees (id INT AUTO_INCREMENT PRIMARY KEY, email VARCHAR(100))";
// $sql = "UPDATE employees SET email='a@b.lk' WHERE id=1";
// $sql = "ALTER TABLE employees ADD salary DECIMAL(10,2)";

// 4. Close Connection
mysqli_close($conn);
?>
```

> [!WARNING] Sanitise + Feedback
> Always `mysqli_real_escape_string($conn, $input)` (or prepared statements) so input is data not code. On success show confirmation/redirect; on error log it, don't expose sensitive info. To refill a form from DB: `value="<?php echo $row['username']; ?>"`.

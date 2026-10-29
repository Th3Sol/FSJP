# Java, Servlet, JSP, JDBC, HTML, CSS and JavaScript Practical Answers (Compact)

> **Notes**
> - Save each Java program in a file matching its `public class` name.
> - Servlet examples use `jakarta.servlet.*` (Tomcat 10+). For Tomcat 9 or older, use `javax.servlet.*`.
> - Run Servlets/JSP on Tomcat. The JDBC example uses MySQL; create the database/table and update the password first.

## Quick Navigation

1. [Student details](#q1-student-details)
2. [Constructor overloading](#q2-constructor-overloading)
3. [Method overloading](#q3-method-overloading)
4. [Single inheritance](#q4-single-inheritance)
5. [Multilevel inheritance](#q5-multilevel-inheritance)
6. [Hierarchical inheritance](#q6-hierarchical-inheritance)
7. [Welcome Servlet](#q7-welcome-servlet)
8. [HTML form with Servlet](#q8-html-form-with-servlet)
9. [Welcome JSP](#q9-welcome-jsp)
10. [Student details JSP](#q10-student-details-jsp)
11. [JDBC CRUD application](#q11-jdbc-crud-application)
12. [Student registration form](#q12-student-registration-form-with-css)
13. [College department webpage](#q13-college-department-webpage)
14. [Email validation](#q14-javascript-email-validation)
15. [Registration form validation](#q15-student-registration-form-validation)
16. [Automatic background change](#q16-change-background-color-every-5-seconds-using-dom)

---

## Q1. Student details

**Aim:** Input and display a student's name, roll number, and marks.

**File: `StudentDetails.java`**

```java
import java.util.Scanner;

public class StudentDetails {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Student s = new Student();
        s.inputDetails(sc);
        s.displayDetails();
        sc.close();
    }
}

class Student {
    String name;
    int rollNumber;
    float marks;

    void inputDetails(Scanner sc) {
        System.out.print("Name: ");
        name = sc.nextLine();
        System.out.print("Roll number: ");
        rollNumber = sc.nextInt();
        System.out.print("Marks: ");
        marks = sc.nextFloat();
    }

    void displayDetails() {
        System.out.println("Name: " + name);
        System.out.println("Roll number: " + rollNumber);
        System.out.println("Marks: " + marks);
    }
}
```

**Result:** The program accepts and displays student details.

---

## Q2. Constructor overloading

**Aim:** Use a default constructor for a welcome message and a parameterized constructor to display a sum.

**File: `Calculator.java`**

```java
public class Calculator {
    Calculator() {
        System.out.println("Welcome to Calculator!");
    }

    Calculator(int a, int b) {
        System.out.println("Sum: " + (a + b));
    }

    public static void main(String[] args) {
        new Calculator();
        new Calculator(10, 20);
    }
}
```

**Result:** Constructor overloading is demonstrated.

---

## Q3. Method overloading

**Aim:** Overload `add()` with no parameters, two integers, and three floats.

**File: `MethodOverloading.java`**

```java
public class MethodOverloading {
    int add() {
        return 5 + 10;
    }

    int add(int a, int b) {
        return a + b;
    }

    float add(float a, float b, float c) {
        return a + b + c;
    }

    public static void main(String[] args) {
        MethodOverloading m = new MethodOverloading();
        System.out.println("Default sum: " + m.add());
        System.out.println("Integer sum: " + m.add(4, 6));
        System.out.println("Float sum: " + m.add(1.5f, 2.5f, 3.0f));
    }
}
```

**Result:** Method overloading is demonstrated using three different parameter lists.

---

## Q4. Single inheritance

**Aim:** Create `Student` as a subclass of `Person`.

**File: `SingleInheritance.java`**

```java
class Person {
    String name;
    int age;
}

class Student extends Person {
    String course;
    int rollNumber;

    void display() {
        System.out.println(name + ", " + age);
        System.out.println(course + ", Roll No: " + rollNumber);
    }
}

public class SingleInheritance {
    public static void main(String[] args) {
        Student s = new Student();
        s.name = "Amit";
        s.age = 19;
        s.course = "Computer Engineering";
        s.rollNumber = 101;
        s.display();
    }
}
```

**Result:** `Student` inherits `name` and `age` from `Person`.

---

## Q5. Multilevel inheritance

**Aim:** Extend `Student` into `GraduateStudent` with `graduationYear`.

**File: `MultilevelInheritance.java`**

```java
class Person {
    String name;
    int age;
}

class Student extends Person {
    String course;
    int rollNumber;
}

class GraduateStudent extends Student {
    int graduationYear;

    void display() {
        System.out.println(name + ", Age: " + age);
        System.out.println(course + ", Roll No: " + rollNumber);
        System.out.println("Graduation Year: " + graduationYear);
    }
}

public class MultilevelInheritance {
    public static void main(String[] args) {
        GraduateStudent g = new GraduateStudent();
        g.name = "Priya";
        g.age = 22;
        g.course = "Computer Science";
        g.rollNumber = 25;
        g.graduationYear = 2027;
        g.display();
    }
}
```

**Result:** Multilevel inheritance is demonstrated: `Person → Student → GraduateStudent`.

---

## Q6. Hierarchical inheritance

**Aim:** Create `Student`, `Teacher`, and `Administrator` subclasses of `Person`.

**File: `HierarchicalInheritance.java`**

```java
class Person {
    String name;
    int age;
    void show() {
        System.out.println(name + ", Age: " + age);
    }
}

class Student extends Person {
    int rollNumber;
    void display() {
        show();
        System.out.println("Roll No: " + rollNumber);
    }
}

class Teacher extends Person {
    String subject;
    void display() {
        show();
        System.out.println("Subject: " + subject);
    }
}

class Administrator extends Person {
    String role;
    void display() {
        show();
        System.out.println("Role: " + role);
    }
}

public class HierarchicalInheritance {
    public static void main(String[] args) {
        Student s = new Student();
        s.name = "Rohan";
        s.age = 18;
        s.rollNumber = 12;

        Teacher t = new Teacher();
        t.name = "Mrs. Sharma";
        t.age = 35;
        t.subject = "Java";

        Administrator a = new Administrator();
        a.name = "Mr. Adam";
        a.age = 42;
        a.role = "Admin";

        s.display();
        t.display();
        a.display();
    }
}
```

**Result:** Multiple classes inherit from the same base class `Person`.

---

## Q7. Welcome Servlet

**Aim:** Display a welcome message in a browser.

**File: `WelcomeServlet.java`**

```java
import java.io.*;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.*;

@WebServlet("/welcome")
public class WelcomeServlet extends HttpServlet {
    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException {
        res.setContentType("text/html");
        res.getWriter().println("<h1>Welcome to Java Servlets!</h1>");
    }
}
```

Run on Tomcat and visit `http://localhost:8080/YourProjectName/welcome`.

**Result:** The Servlet displays a welcome message.

---

## Q8. HTML form with Servlet

**Aim:** Accept a user's name from an HTML form and display it.

### File 1: `name-form.html`

```html
<!DOCTYPE html>
<html>
<body>
    <form action="display-name" method="post">
        Name: <input name="name" required>
        <button type="submit">Submit</button>
    </form>
</body>
</html>
```

### File 2: `DisplayNameServlet.java`

```java
import java.io.*;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.*;

@WebServlet("/display-name")
public class DisplayNameServlet extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws IOException {
        res.setContentType("text/html;charset=UTF-8");
        String name = req.getParameter("name");
        if (name == null || name.trim().isEmpty()) {
            name = "Guest";
        }

        // Escape HTML special characters before displaying user input.
        name = name.replace("&", "&amp;").replace("<", "&lt;")
                   .replace(">", "&gt;").replace("\\"", "&quot;")
                   .replace("'", "&#39;");
        res.getWriter().println("<h2>Welcome, " + name + "!</h2>");
    }
}
```

**Result:** The Servlet receives and displays the submitted name.

---

## Q9. Welcome JSP

**Aim:** Display a welcome message using JSP.

**File: `welcome.jsp`**

```jsp
<%@ page contentType="text/html;charset=UTF-8" %>
<html>
<body>
    <h1>Welcome to JavaServer Pages (JSP)!</h1>
</body>
</html>
```

**Result:** JSP displays the welcome message in a browser.

---

## Q10. Student details JSP

**Aim:** Display name, register number, and department.

**File: `student.jsp`**

```jsp
<%@ page contentType="text/html;charset=UTF-8" %>
<html>
<body>
    <h2>Student Details</h2>
    <p>Name: Rahul</p>
    <p>Register Number: 123456</p>
    <p>Department: Computer Engineering</p>
</body>
</html>
```

Replace the sample details with your own.

**Result:** The JSP page displays the student's details.

---

## Q11. JDBC CRUD application

**Aim:** Insert, update, delete, and display student records using JDBC.

### Step 1: Create database

```sql
CREATE DATABASE college;
USE college;
CREATE TABLE students (
    roll_no INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    marks FLOAT NOT NULL
);
```

### Step 2: Java program

**File: `StudentJDBC.java`**

> Add MySQL Connector/J to your classpath and set your database password below.

```java
import java.sql.*;
import java.util.Scanner;

public class StudentJDBC {
    static final String URL = "jdbc:mysql://localhost:3306/college";
    static final String USER = "root";
    static final String PASS = "your_password";

    static Connection connect() throws SQLException {
        return DriverManager.getConnection(URL, USER, PASS);
    }

    static void insert(Scanner sc) throws SQLException {
        System.out.print("Roll, name, marks: ");
        int roll = sc.nextInt();
        sc.nextLine();
        String name = sc.nextLine();
        float marks = sc.nextFloat();

        try (Connection c = connect();
             PreparedStatement p = c.prepareStatement(
                 "INSERT INTO students VALUES (?, ?, ?)")) {
            p.setInt(1, roll);
            p.setString(2, name);
            p.setFloat(3, marks);
            p.executeUpdate();
            System.out.println("Inserted.");
        }
    }

    static void update(Scanner sc) throws SQLException {
        System.out.print("Roll number and new marks: ");
        int roll = sc.nextInt();
        float marks = sc.nextFloat();

        try (Connection c = connect();
             PreparedStatement p = c.prepareStatement(
                 "UPDATE students SET marks=? WHERE roll_no=?")) {
            p.setFloat(1, marks);
            p.setInt(2, roll);
            System.out.println(p.executeUpdate() > 0 ? "Updated." : "Not found.");
        }
    }

    static void delete(Scanner sc) throws SQLException {
        System.out.print("Roll number to delete: ");
        int roll = sc.nextInt();

        try (Connection c = connect();
             PreparedStatement p = c.prepareStatement(
                 "DELETE FROM students WHERE roll_no=?")) {
            p.setInt(1, roll);
            System.out.println(p.executeUpdate() > 0 ? "Deleted." : "Not found.");
        }
    }

    static void display() throws SQLException {
        try (Connection c = connect();
             Statement s = c.createStatement();
             ResultSet r = s.executeQuery("SELECT * FROM students")) {
            while (r.next())
                System.out.println(
                    r.getInt("roll_no") + " | "
                    + r.getString("name") + " | "
                    + r.getFloat("marks")
                );
        }
    }

    public static void main(String[] args) {
        try (Scanner sc = new Scanner(System.in)) {
            while (true) {
                System.out.print("\\n1.Insert 2.Update 3.Delete 4.Display 5.Exit: ");
                int choice = sc.nextInt();
                try {
                    switch (choice) {
                        case 1:
                            insert(sc);
                            break;
                        case 2:
                            update(sc);
                            break;
                        case 3:
                            delete(sc);
                            break;
                        case 4:
                            display();
                            break;
                        case 5:
                            return;
                        default:
                            System.out.println("Invalid choice.");
                    }
                } catch (SQLException e) {
                    System.out.println("Database error: " + e.getMessage());
                }
            }
        }
    }
}
```

**Result:** The menu-driven JDBC program supports insert, update, delete, and display operations.

---

## Q12. Student registration form with CSS

**Aim:** Create a styled student registration form.

**File: `registration.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Student Registration</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #eef2f7;
        }

        form {
            max-width: 400px;
            margin: 30px auto;
            padding: 22px;
            background: white;
            border-radius: 10px;
        }

        input, select, button {
            box-sizing: border-box;
            width: 100%;
            padding: 10px;
            margin: 7px 0;
        }

        button {
            background: #175cd3;
            color: white;
            border: 0;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <form>
        <h2>Student Registration</h2>
        <input name="name" placeholder="Full name" required>
        <input type="email" name="email" placeholder="Email" required>
        <input name="roll" placeholder="Roll number" required>
        <select name="course" required>
            <option value="">Select course</option>
            <option>Computer Engineering</option>
            <option>Information Technology</option>
            <option>Mechanical Engineering</option>
        </select>
        <input type="tel" name="phone" placeholder="10-digit mobile number"
               pattern="[0-9]{10}" required>
        <button type="submit">Register</button>
    </form>
</body>
</html>
```

**Result:** A CSS-styled student registration form is displayed.

---

## Q13. College department webpage

**Aim:** Display faculty details, course information, and contact details.

**File: `department.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Computer Engineering Department</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            background: #f4f7fb;
            color: #222;
        }

        header, footer {
            background: #173b70;
            color: white;
            text-align: center;
            padding: 18px;
        }

        nav {
            background: #102a50;
            padding: 10px;
            text-align: center;
        }

        nav a {
            color: white;
            margin: 10px;
        }

        section {
            background: white;
            margin: 18px auto;
            padding: 18px;
            max-width: 800px;
            border-radius: 8px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            border: 1px solid #aaa;
            padding: 8px;
            text-align: left;
        }
    </style>
</head>
<body>
    <header>
        <h1>ABC College of Engineering</h1>
        <h2>Computer Engineering Department</h2>
    </header>
    <nav>
        <a href="#faculty">Faculty</a>
        <a href="#courses">Courses</a>
        <a href="#contact">Contact</a>
    </nav>

    <section>
        <h2>About</h2>
        <p>The department teaches programming, databases, networking and web development.</p>
    </section>

    <section id="faculty">
        <h2>Faculty Details</h2>
        <table>
            <tr><th>Name</th><th>Designation</th><th>Subject</th></tr>
            <tr><td>Dr. Sharma</td><td>HOD</td><td>Networks</td></tr>
            <tr><td>Prof. Smith</td><td>Lecturer</td><td>Java</td></tr>
        </table>
    </section>

    <section id="courses">
        <h2>Courses</h2>
        <ul><li>Java</li><li>DBMS</li><li>Computer Networks</li><li>Web Development</li></ul>
    </section>

    <section id="contact">
        <h2>Contact</h2>
        <p>Address: ABC College, Your City</p>
        <p>Email: computer@example.com</p>
        <p>Phone: 00000 00000</p>
    </section>

    <footer>&copy; 2026 ABC College</footer>
</body>
</html>
```

**Result:** The webpage contains faculty, course, and contact information.

---

## Q14. JavaScript email validation

**Aim:** Check whether an entered email address has a valid basic format.

**File: `email-validation.html`**

```html
<!DOCTYPE html>
<html>
<body>
    <h2>Email Validation</h2>
    <input id="email" placeholder="Enter email">
    <button onclick="validateEmail()">Check</button>
    <p id="result"></p>

    <script>
        function validateEmail() {
            let e = document.getElementById("email").value.trim();
        let pattern = /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/;

        if (pattern.test(e)) {
            document.getElementById("result").textContent = "Valid email";
        } else {
            document.getElementById("result").textContent = "Invalid email";
        }
        }
    </script>
</body>
</html>
```

**Result:** The program displays whether the email matches a basic email pattern.

---

## Q15. Student registration form validation

**Aim:** Validate name, email, and password using JavaScript.

**File: `form-validation.html`**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Registration Validation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #eef2f7;
        }

        form {
            max-width: 350px;
            margin: 30px auto;
            padding: 20px;
            background: white;
        }

        input, button {
            box-sizing: border-box;
            width: 100%;
            padding: 9px;
            margin: 7px 0;
        }
    </style>
</head>
<body>
    <form id="form">
        <h2>Student Registration</h2>
        <input id="name" placeholder="Name" required>
        <input id="email" placeholder="Email" required>
        <input id="password" type="password" placeholder="Password" required>
        <button>Register</button>
        <p id="msg"></p>
    </form>

    <script>
        document.getElementById("form").onsubmit = function(e) {
            e.preventDefault();
            let n = document.getElementById("name").value.trim();
            let mail = document.getElementById("email").value.trim();
            let pass = document.getElementById("password").value;
            let msg = document.getElementById("msg");

            if (n.length < 2) {
                msg.textContent = "Enter a valid name.";
            } else if (!/^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/.test(mail)) {
                msg.textContent = "Enter a valid email.";
            } else if (pass.length < 8) {
                msg.textContent = "Password must be at least 8 characters.";
            } else {
                msg.textContent = "Registration details are valid.";
            }
        };
    </script>
</body>
</html>
```

**Result:** The form checks the name, email format, and password length. Real applications should also validate on the server.

---

## Q16. Change background color every 5 seconds using DOM

**Aim:** Automatically change the background color every five seconds.

**File: `background-change.html`**

```html
<!DOCTYPE html>
<html>
<body>
    <h2>Background changes every 5 seconds</h2>
    <script>
        const colors = [
            "lightblue",
            "lightgreen",
            "lightyellow",
            "lightpink",
            "lavender"
        ];
        let i = 0;

        setInterval(() => {
            document.body.style.backgroundColor = colors[i];
            i = (i + 1) % colors.length;
        }, 5000);
    </script>
</body>
</html>
```

**Result:** The DOM changes the page background automatically every five seconds without user action.

---

## End

All 16 practical answers are included in compact form. Save each HTML example separately and open it in a browser. Run Java programs using a JDK, and deploy Servlet/JSP programs on Tomcat. For JDBC, configure MySQL and its JDBC driver first.

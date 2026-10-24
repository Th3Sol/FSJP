# Java, JavaScript, DOM and React Practical Programs

## 1. Find the area of circle, square and rectangle using class and objects

```java
class Area {
    void circle(double r) {
        System.out.println("Area of Circle: " + (3.14 * r * r));
    }

    void square(double side) {
        System.out.println("Area of Square: " + (side * side));
    }

    void rectangle(double length, double breadth) {
        System.out.println("Area of Rectangle: " + (length * breadth));
    }

    public static void main(String[] args) {
        Area a = new Area();
        a.circle(4);
        a.square(5);
        a.rectangle(6, 3);
    }
}
```

## 2. Store and display student details using class and objects

```java
class Student {
    String name = "Rahul";
    int rollNo = 101;
    String branch = "Computer Engineering";

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Roll Number: " + rollNo);
        System.out.println("Branch: " + branch);
    }

    public static void main(String[] args) {
        Student s = new Student();
        s.display();
    }
}
```

## 3. Check whether a number is even or odd

```java
import java.util.Scanner;

public class EvenOdd {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int n = sc.nextInt();

        if (n % 2 == 0)
            System.out.println("Even number");
        else
            System.out.println("Odd number");

        sc.close();
    }
}
```

## 4. Find the maximum of two numbers using method overloading (`int` and `double`)

```java
class Maximum {
    int max(int a, int b) {
        return (a > b) ? a : b;
    }

    double max(double a, double b) {
        return (a > b) ? a : b;
    }

    public static void main(String[] args) {
        Maximum m = new Maximum();
        System.out.println("Maximum integer: " + m.max(10, 20));
        System.out.println("Maximum double: " + m.max(5.5, 2.8));
    }
}
```

## 5. Constructor overloading for an Employee class

```java
class Employee {
    String name;
    double salary;

    Employee() {
        name = "Unknown";
        salary = 0;
    }

    Employee(String n) {
        name = n;
        salary = 0;
    }

    Employee(String n, double s) {
        name = n;
        salary = s;
    }

    void display() {
        System.out.println("Name: " + name + ", Salary: " + salary);
    }

    public static void main(String[] args) {
        Employee e1 = new Employee();
        Employee e2 = new Employee("Amit");
        Employee e3 = new Employee("Priya", 25000);

        e1.display();
        e2.display();
        e3.display();
    }
}
```

## 6. Overload `add()` to sum two or three integers

```java
class Addition {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    public static void main(String[] args) {
        Addition obj = new Addition();
        System.out.println("Sum of two numbers: " + obj.add(10, 20));
        System.out.println("Sum of three numbers: " + obj.add(10, 20, 30));
    }
}
```

## 7. Constructor overloading for Student name and grade

```java
class Student {
    String name;
    char grade;

    Student(String n) {
        name = n;
        grade = '-';
    }

    Student(String n, char g) {
        name = n;
        grade = g;
    }

    void display() {
        System.out.println("Name: " + name + ", Grade: " + grade);
    }

    public static void main(String[] args) {
        Student s1 = new Student("Asha");
        Student s2 = new Student("Rohan", 'A');
        s1.display();
        s2.display();
    }
}
```

## 8. Multilevel inheritance: Person → Employee → Manager

```java
class Person {
    void showPerson() {
        System.out.println("I am a person");
    }
}

class Employee extends Person {
    void showEmployee() {
        System.out.println("I am an employee");
    }
}

class Manager extends Employee {
    void showManager() {
        System.out.println("I am a manager");
    }

    public static void main(String[] args) {
        Manager m = new Manager();
        m.showPerson();
        m.showEmployee();
        m.showManager();
    }
}
```

## 9. Handle division by zero using try and catch

```java
public class ArithmeticExceptionDemo {
    public static void main(String[] args) {
        try {
            int a = 10, b = 0;
            System.out.println("Result: " + (a / b));
        } catch (ArithmeticException e) {
            System.out.println("Error: Cannot divide by zero.");
        }
    }
}
```

## 10. Interactive Biodata/Profile webpage using HTML, CSS and JavaScript

Save as `biodata.html` and open it in a browser. Replace the sample details with your own.

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Biodata</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #eef2f7;
            color: #222;
            margin: 30px;
        }
        .card {
            max-width: 650px;
            margin: auto;
            padding: 24px;
            background: white;
            border-radius: 12px;
        }
        button {
            padding: 9px 14px;
            margin: 5px;
            cursor: pointer;
        }
        .dark {
            background: #222;
            color: white;
        }
        .dark .card {
            background: #333;
        }
    </style>
</head>
<body>
    <div class="card">
        <h1 id="name">My Biodata</h1>
        <button onclick="welcome()">Welcome</button>
        <button onclick="toggleTheme()">Change Theme</button>
        <button onclick="toggleDetails()">Show/Hide Details</button>
        <p id="message"></p>

        <div id="details">
            <h2>Personal Details</h2>
            <p>Name: Your Name</p>
            <p>Course: Engineering</p>

            <h2>Educational Qualifications</h2>
            <p>Currently pursuing Engineering.</p>

            <h2>Skills</h2>
            <p>Java, HTML, CSS, JavaScript</p>

            <h2>Hobbies</h2>
            <p>Coding, reading, music and sports</p>

            <h2>Achievements</h2>
            <p>Add your achievements here.</p>
        </div>
        <p id="date"></p>
    </div>

    <script>
        function welcome() {
            document.getElementById("message").textContent =
                "Welcome to my profile!";
        }

        function toggleTheme() {
            document.body.classList.toggle("dark");
        }

        function toggleDetails() {
            const details = document.getElementById("details");
            details.style.display =
                details.style.display === "none" ? "block" : "none";
        }

        document.getElementById("date").textContent =
            "Current date and time: " + new Date().toLocaleString();
    </script>
</body>
</html>
```

## 11. Check whether a bank withdrawal is possible

```html
<!DOCTYPE html>
<html>
<head><title>Bank Withdrawal</title></head>
<body>
    <h2>Bank Withdrawal Check</h2>
    <label>Account Balance: <input type="number" id="balance"></label><br><br>
    <label>Withdrawal Amount: <input type="number" id="amount"></label><br><br>
    <button onclick="checkWithdrawal()">Check</button>
    <p id="result"></p>

    <script>
        function checkWithdrawal() {
            let balance = Number(document.getElementById("balance").value);
            let amount = Number(document.getElementById("amount").value);

            if (balance < 0 || amount <= 0) {
                document.getElementById("result").textContent =
                    "Enter valid amounts.";
            } else if (amount <= balance) {
                document.getElementById("result").textContent =
                    "Withdrawal is possible.";
            } else {
                document.getElementById("result").textContent =
                    "Insufficient balance.";
            }
        }
    </script>
</body>
</html>
```

## 12. Check voting eligibility using age

```html
<!DOCTYPE html>
<html>
<head><title>Voting Eligibility</title></head>
<body>
    <h2>Voting Eligibility Check</h2>
    <label>Enter age: <input type="number" id="age"></label>
    <button onclick="checkAge()">Check</button>
    <p id="result"></p>

    <script>
        function checkAge() {
            let age = Number(document.getElementById("age").value);

            if (age < 0 || document.getElementById("age").value === "") {
                document.getElementById("result").textContent =
                    "Enter a valid age.";
            } else if (age >= 18) {
                document.getElementById("result").textContent =
                    "You are eligible to vote.";
            } else {
                document.getElementById("result").textContent =
                    "You are not eligible to vote.";
            }
        }
    </script>
</body>
</html>
```

## 13. Validate an email address (`@` and `.`)

```html
<!DOCTYPE html>
<html>
<head><title>Email Validation</title></head>
<body>
    <h2>Email Validation</h2>
    <input type="text" id="email" placeholder="Enter email">
    <button onclick="validateEmail()">Submit</button>

    <script>
        function validateEmail() {
            let email = document.getElementById("email").value;

            while (!email.includes("@") || !email.includes(".")) {
                alert("Invalid email. Please enter an email containing @ and .");
                email = prompt("Re-enter your email address:") || "";
                if (email === "") {
                    alert("Email entry cancelled.");
                    return;
                }
            }

            document.getElementById("email").value = email;
            alert("Email accepted.");
        }
    </script>
</body>
</html>
```

## 14. Validate a 6-digit OTP

```html
<!DOCTYPE html>
<html>
<head><title>OTP Validation</title></head>
<body>
    <h2>OTP Validation</h2>
    <input type="text" id="otp" maxlength="6" placeholder="Enter 6-digit OTP">
    <button onclick="validateOTP()">Validate</button>
    <p id="result"></p>

    <script>
        function validateOTP() {
            let otp = document.getElementById("otp").value;

            if (/^[0-9]{6}$/.test(otp)) {
                document.getElementById("result").textContent = "Valid OTP format.";
            } else {
                document.getElementById("result").textContent =
                    "Invalid OTP. Enter exactly 6 digits.";
            }
        }
    </script>
</body>
</html>
```

## 15. Validate a mobile number

```html
<!DOCTYPE html>
<html>
<head><title>Mobile Number Validation</title></head>
<body>
    <h2>Mobile Number Validation</h2>
    <input type="text" id="mobile" maxlength="10" placeholder="Enter 10-digit mobile number">
    <button onclick="validateMobile()">Validate</button>
    <p id="result"></p>

    <script>
        function validateMobile() {
            let mobile = document.getElementById("mobile").value;

            if (/^[6-9][0-9]{9}$/.test(mobile)) {
                document.getElementById("result").textContent =
                    "Valid mobile number.";
            } else {
                document.getElementById("result").textContent =
                    "Invalid mobile number.";
            }
        }
    </script>
</body>
</html>
```

## 16. Show or hide a password using DOM

```html
<!DOCTYPE html>
<html>
<head><title>Show/Hide Password</title></head>
<body>
    <h2>Password</h2>
    <input type="password" id="password" placeholder="Enter password">
    <button onclick="togglePassword()">Show</button>

    <script>
        function togglePassword() {
            let input = document.getElementById("password");
            let button = document.querySelector("button");

            if (input.type === "password") {
                input.type = "text";
                button.textContent = "Hide";
            } else {
                input.type = "password";
                button.textContent = "Show";
            }
        }
    </script>
</body>
</html>
```

## 17. Change webpage to dark mode using DOM

```html
<!DOCTYPE html>
<html>
<head>
    <title>Dark Mode</title>
    <style>
        body { font-family: Arial; padding: 30px; }
        .dark { background: #222; color: white; }
    </style>
</head>
<body>
    <h2>Dark Mode Demo</h2>
    <p>Click the button to change the theme.</p>
    <button onclick="document.body.classList.toggle('dark')">
        Toggle Dark Mode
    </button>
</body>
</html>
```

## 18. Change webpage background color every 5 seconds using DOM

```html
<!DOCTYPE html>
<html>
<head><title>Automatic Background Color</title></head>
<body>
    <h2>Background Color Changes Every 5 Seconds</h2>

    <script>
        const colors = ["lightblue", "lightgreen", "lightyellow",
                        "lightpink", "lavender"];
        let index = 0;

        setInterval(function() {
            document.body.style.backgroundColor = colors[index];
            index = (index + 1) % colors.length;
        }, 5000);
    </script>
</body>
</html>
```

## 19. Show and hide a website menu using DOM

```html
<!DOCTYPE html>
<html>
<head>
    <title>Show/Hide Menu</title>
    <style>
        #menu { background: #eee; padding: 15px; width: 150px; }
        #menu a { display: block; padding: 6px; }
    </style>
</head>
<body>
    <h2>Website Menu</h2>
    <button onclick="toggleMenu()">Show/Hide Menu</button>

    <div id="menu">
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </div>

    <script>
        function toggleMenu() {
            let menu = document.getElementById("menu");
            menu.style.display = menu.style.display === "none" ? "block" : "none";
        }
    </script>
</body>
</html>
```

## 20. React app: accept a name and display a greeting using `useState`

```jsx
import { useState } from "react";

function App() {
    const [name, setName] = useState("");

    return (
        <div>
            <h2>Greeting App</h2>
            <input
                type="text"
                placeholder="Enter your name"
                value={name}
                onChange={(e) => setName(e.target.value)}
            />
            <h3>Hello, {name || "Guest"}!</h3>
        </div>
    );
}

export default App;
```

## 21. React app: display student information using components and props

```jsx
function Student(props) {
    return (
        <div>
            <h2>Student Information</h2>
            <p>Name: {props.name}</p>
            <p>Roll Number: {props.rollNo}</p>
            <p>Branch: {props.branch}</p>
        </div>
    );
}

function App() {
    return (
        <Student
            name="Rahul"
            rollNo="101"
            branch="Computer Engineering"
        />
    );
}

export default App;
```

## 22. React app: color buttons using Hooks and event handling

```jsx
import { useState } from "react";

function App() {
    const [message, setMessage] = useState("");

    return (
        <div>
            <h2>Select a Color</h2>
            <button onClick={() => setMessage("You selected Red")}>Red</button>
            <button onClick={() => setMessage("You selected Blue")}>Blue</button>
            <button onClick={() => setMessage("You selected Green")}>Green</button>
            <button onClick={() => setMessage("You selected Yellow")}>Yellow</button>
            <p>{message}</p>
        </div>
    );
}

export default App;
```

## 23. React app: show and hide a message using a button

```jsx
import { useState } from "react";

function App() {
    const [show, setShow] = useState(false);

    return (
        <div>
            <h2>Show/Hide Message</h2>
            <button onClick={() => setShow(!show)}>
                {show ? "Hide Message" : "Show Message"}
            </button>

            {show && <p>Hello! This is a hidden message.</p>}
        </div>
    );
}

export default App;
```

---

**Notes:**
- For Java programs, save each program in a `.java` file whose name matches its `public` class, if present.
- For Questions 10–19, save each HTML program in its own `.html` file and open it in a browser.
- For Questions 20–23, place the code in `App.jsx` in a React project created with a tool such as Vite. These are component examples, not standalone HTML files.

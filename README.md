# Employee Management System  

A complete desktop-based application built using Java Swing and MySQL to efficiently manage employee records. This system allows HR/admin users to add, update, view, and remove employee details through an intuitive graphical interface.

---

## Features

### Authentication
- Login system using MySQL `login` table.
- Extendable for admin/user roles.

### Employee Management
- Add new employees with full personal, professional, and contact details.
- Update existing employee information.
- View all employees in a table format.
- Delete employees from the system.
- Auto-generated unique Employee ID.

### Additional Functionalities
- Date Picker using JDateChooser.
- ResultSet to JTable conversion using DbUtils.
- Splash screen and modern GUI design.
- Clean and structured Swing UI.

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| UI | Java Swing |
| Backend | Core Java |
| Database | MySQL |
| Libraries | MySQL Connector/J, JCalendar, rs2xml (DbUtils) |
| IDE | IntelliJ IDEA / NetBeans |

---

## Project Structure

Employee-Management-System/
├── src/
│ └── employee/management/system/
│ ├── AddEmployee.java
│ ├── UpdateEmployee.java
│ ├── ViewEmployee.java
│ ├── RemoveEmployee.java
│ ├── Login.java
│ ├── Home.java
│ ├── Conn.java
│ ├── Splash.java
│ └── ...
└── README.md

yaml
Copy code

---

## Database Setup

Run the following SQL scripts:

### 1. Create Database
```sql
CREATE DATABASE employee_management;
USE employee_management;
2. Create Login Table
sql
Copy code
CREATE TABLE login (
    username VARCHAR(50) PRIMARY KEY,
    password VARCHAR(100)
);
Insert an admin user:

sql
Copy code
INSERT INTO login VALUES ("admin", "admin123");
3. Create Employee Table
sql
Copy code
CREATE TABLE employee (
    name VARCHAR(50),
    fname VARCHAR(50),
    dob VARCHAR(50),
    salary VARCHAR(20),
    address VARCHAR(100),
    phone VARCHAR(20),
    email VARCHAR(50),
    education VARCHAR(20),
    designation VARCHAR(50),
    aadhar VARCHAR(20),
    empid VARCHAR(20) PRIMARY KEY
);
How to Run the Project Locally
1. Clone the Repository
bash
Copy code
git clone https://github.com/Subhasis19/Employee-Management-System.git
2. Open the Project in IntelliJ IDEA or NetBeans
3. Add Required Libraries
mysql-connector-j-x.x.x.jar

jcalendar-1.4.jar

rs2xml.jar

4. Configure Database Credentials
Update MySQL connection details inside Conn.java:

java
Copy code
c = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/employee_management",
    "root",
    "your_mysql_password"
);
5. Run the Application
Run Splash.java to start the system.

Future Improvements
Secure password hashing and role-based authentication.

Export employee data to PDF or Excel.

Advanced search, filters, and sorting.

Attendance and payroll modules.

Updated UI using FlatLaf or JavaFX.

Author
Subhasis Samantasinghar
LinkedIn: [Add your link here]
GitHub: https://github.com/Subhasis19

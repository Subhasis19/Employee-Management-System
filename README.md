# Employee Management System

## Overview

The Employee Management System is a comprehensive desktop application designed to streamline HR and administrative operations. Built with Java Swing and MySQL, it provides a secure and user-friendly platform for managing employee records, including personal information, employment details, and contact information.

---

## Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation Guide](#installation-guide)
- [Database Configuration](#database-configuration)
- [Project Structure](#project-structure)
- [Usage Instructions](#usage-instructions)
- [Future Enhancements](#future-enhancements)
- [Author](#author)

---

## Features

### Authentication & Security
- Secure login system with MySQL-backed authentication
- User credential verification against the `login` table
- Foundation for role-based access control (RBAC)

### Employee Management
- **Add Employees**: Create new employee records with comprehensive details
  - Personal Information: Name, date of birth, identification numbers
  - Professional Details: Designation, salary, education level
  - Contact Information: Phone, email, address
  - Auto-generated unique Employee IDs
  
- **View Employees**: Display all employee records in a searchable, sortable table format
- **Update Employees**: Modify existing employee information
- **Remove Employees**: Delete employee records from the system

### User Interface
- Intuitive graphical interface built with Java Swing
- Interactive date picker using JDateChooser
- Splash screen for professional application startup
- Responsive table views with DbUtils integration
- Clean, organized UI layout

---

## Technology Stack

| Component | Technology |
|-----------|-----------|
| **Frontend** | Java Swing |
| **Backend Logic** | Core Java |
| **Database** | MySQL (5.7 or higher) |
| **Key Libraries** | MySQL Connector/J, JCalendar, rs2xml (DbUtils) |
| **Supported IDEs** | IntelliJ IDEA, NetBeans, Eclipse |
| **Java Version** | JDK 8 or higher |

---

## Prerequisites

Before installing the Employee Management System, ensure you have:

1. **Java Development Kit (JDK)**
   - Version 8 or higher
   - Verify installation: `java -version`

2. **MySQL Server**
   - Version 5.7 or higher
   - Download from: https://www.mysql.com/downloads/
   - Verify installation: `mysql --version`

3. **Git**
   - For cloning the repository
   - Download from: https://git-scm.com/

4. **IDE (Optional but Recommended)**
   - IntelliJ IDEA (Community or Professional)
   - NetBeans
   - Eclipse IDE for Java Developers

---

## Installation Guide

### Step 1: Clone the Repository

```bash
git clone https://github.com/Subhasis19/Employee-Management-System.git
cd Employee-Management-System
```

### Step 2: Set Up Java Development Environment

Verify Java is properly installed:

```bash
java -version
javac -version
```

If not installed, download and install from [oracle.com](https://www.oracle.com/java/technologies/downloads/) or use your package manager.

### Step 3: Start MySQL Server

**On Linux/Mac:**
```bash
mysql.server start
```

**On Windows:**
```cmd
net start MySQL80
```

Verify MySQL is running:
```bash
mysql -u root -p -e "SELECT 1"
```

### Step 4: Download and Configure Required Libraries

Create a `lib` directory in the project root:

```bash
mkdir lib
```

Download the following JAR files and place them in the `lib` directory:

1. **MySQL Connector/J** (8.0.33 or latest)
   - Download: https://dev.mysql.com/downloads/connector/j/
   - File: `mysql-connector-j-8.0.33.jar`

2. **JCalendar** (1.4)
   - Download: https://www.toedter.com/jcalendar/
   - File: `jcalendar-1.4.jar`

3. **DbUtils (rs2xml)**
   - Download: https://github.com/orionhealth/rs2xml
   - File: `rs2xml.jar`

### Step 5: Configure the IDE

#### For IntelliJ IDEA:

1. Open the project in IntelliJ IDEA
2. Go to **File** → **Project Structure** → **Libraries**
3. Click the **+** button and select **Java**
4. Navigate to the `lib` folder and select all JAR files
5. Click **Apply** → **OK**

#### For NetBeans:

1. Open the project in NetBeans
2. Right-click the project → **Properties**
3. Go to **Libraries** → **Compile** tab
4. Click **Add JAR/Folder** and select all files from the `lib` directory
5. Click **OK**

#### For Eclipse:

1. Right-click the project → **Build Path** → **Configure Build Path**
2. Go to the **Libraries** tab
3. Click **Add External JARs** and select files from the `lib` directory
4. Click **Apply and Close**

### Step 6: Database Configuration

#### Create Database and Tables

Open a terminal and connect to MySQL:

```bash
mysql -u root -p
```

Execute the following SQL commands:

```sql
-- Create Database
CREATE DATABASE employee_management;
USE employee_management;

-- Create Login Table
CREATE TABLE login (
    username VARCHAR(50) PRIMARY KEY,
    password VARCHAR(100)
);

-- Insert Admin User
INSERT INTO login VALUES ("admin", "admin123");

-- Create Employee Table
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
```

#### Update Database Connection Settings

Navigate to `src/employee/management/system/Conn.java` and update the connection parameters:

```java
String url = "jdbc:mysql://localhost:3306/employee_management";
String user = "root";
String password = "your_mysql_password";  // Replace with your MySQL password

c = DriverManager.getConnection(url, user, password);
```

---

## Project Structure

```
Employee-Management-System/
├── src/
│   ├── employee/
│   │   └── management/
│   │       └── system/
│   │           ├── Splash.java                # Application startup screen
│   │           ├── Login.java                 # User authentication
│   │           ├── Home.java                  # Main dashboard
│   │           ├── AddEmployee.java           # Add new employee
│   │           ├── UpdateEmployee.java        # Update employee details
│   │           ├── ViewEmployee.java          # Display all employees
│   │           ├── RemoveEmployee.java        # Delete employees
│   │           ├── Conn.java                  # Database connection
│   │           └── ...
│   └── icons/                                 # UI icons and resources
├── lib/                                       # External libraries (JAR files)
├── README.md                                  # Project documentation
└── .gitignore
```

---

## Usage Instructions

### Launching the Application

1. **Compile the Project:**
   ```bash
   javac -cp "lib/*" src/employee/management/system/*.java
   ```

2. **Run the Application:**
   ```bash
   java -cp "lib/*:src" employee.management.system.Splash
   ```

   Or directly from your IDE:
   - Right-click `Splash.java` → **Run**

### Login Credentials

**Default Admin User:**
- Username: `admin`
- Password: `admin123`

### Application Features

1. **Login**: Authenticate using valid credentials
2. **Add Employee**: Enter employee details and generate unique ID
3. **View Employees**: Browse all employee records in table format
4. **Update Employee**: Modify existing employee information
5. **Remove Employee**: Delete employee records
6. **Logout**: Exit the application securely

---

## Future Enhancements

The following features are planned for future releases:

- **Security Improvements**
  - Password hashing and encryption
  - Role-based access control (Admin/User)
  - Audit logging and activity tracking

- **Data Management**
  - Export to PDF and Excel formats
  - Advanced search and filtering capabilities
  - Data sorting and pagination
  - Backup and restore functionality

- **Feature Expansion**
  - Attendance management module
  - Payroll processing system
  - Performance evaluation tools
  - Leave management system

- **User Interface**
  - Modern Look and Feel (FlatLaf)
  - Migration to JavaFX
  - Responsive design improvements
  - Dark mode support

---

## Troubleshooting

**Issue: "Cannot connect to database"**
- Verify MySQL is running
- Check database credentials in `Conn.java`
- Ensure database `employee_management` exists

**Issue: "JAR files not found"**
- Confirm all library files are in the `lib` directory
- Rebuild the project and check build path configuration

**Issue: "Login fails with correct credentials"**
- Verify the `login` table exists in the database
- Check that admin user was inserted correctly
- Review database connection settings

---

## Author

**Subhasis Samantasinghar**

- GitHub: [https://github.com/Subhasis19](https://github.com/Subhasis19)
- LinkedIn: [[Add your LinkedIn profile](https://www.linkedin.com/in/subhasis-samantasinghar/)]
- Email: [asubhasis2002@gmail.com]

---

## Support

For issues, questions, or contributions, please visit the [GitHub Repository](https://github.com/Subhasis19/Employee-Management-System) or contact the author directly.

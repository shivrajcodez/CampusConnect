# 🎓 Student Management System

A full-stack web application built with Core Java, JDBC, Servlet, JSP and MySQL.  
Developed as part of the **SPPU Third Year PAT (Project Based Assessment)** internship project.

🌐 **Live Demo:** [campusconnect-production-45d8.up.railway.app](https://campusconnect-production-45d8.up.railway.app)

---

## 🔐 Demo Credentials

| Role    | Username       | Password     |
|---------|---------------|--------------|
| Admin   | `admin`        | `admin123`   |
| Student | `rahul.sharma` | `student123` |
| Student | `priya.patil`  | `student123` |

---

## ✨ Features

### Admin Panel
- 🔐 Secure login with session management
- 📊 Dashboard with total students and courses count
- 👨‍🎓 Add, Edit, Delete, View Students (full CRUD)
- 🔍 Search students by name, email, enrollment number, department
- 📚 Course Management (Add, Edit, Delete courses)
- 📝 Marks Entry with automatic grade calculation
- 📅 Attendance Tracking (Present / Absent / Late)
- 🖨️ Print student records

### Student Portal
- 🔐 Secure login with personal session
- 🏠 Personal dashboard with profile info
- 📚 View enrolled courses
- 📝 View personal marks and grades
- 📅 View attendance with percentage
- ⚠️ Warning if attendance below 75%

### Validation
- ✅ Indian mobile number validation (10 digits, starts with 6-9)
- ✅ Email format validation (frontend + backend)
- ✅ Duplicate email and phone detection
- ✅ Marks range validation (0-50 each)
- ✅ Bootstrap form validation with live feedback

---

## 🛠️ Tech Stack

| Layer      | Technology                        |
|------------|-----------------------------------|
| Frontend   | JSP, HTML5, CSS3, Bootstrap 5     |
| Backend    | Core Java, Servlets               |
| Database   | MySQL, JDBC                       |
| Server     | Apache Tomcat 9                   |
| Hosting    | Railway.app (Docker)              |
| IDE        | Eclipse IDE for Enterprise Java   |

---

## 🗄️ Database Schema
```
users        → user_id, username, password, role
students     → student_id, name, email, phone, enrollment_number, department, year
courses      → course_id, course_name, course_code, department, credits, semester
enrollments  → enrollment_id, student_id, course_id (junction table)
marks        → mark_id, student_id, course_id, internal, external, total, grade
attendance   → attendance_id, student_id, course_id, date, status
```

---

## 📁 Project Structure
```
StudentManagementSystem/
├── src/
│   └── com/sms/
│       ├── model/        → Student.java, User.java, Course.java, Marks.java, Attendance.java
│       ├── dao/          → StudentDAO.java, UserDAO.java, CourseDAO.java, MarksDAO.java, AttendanceDAO.java
│       ├── servlet/      → LoginServlet, StudentServlet, CourseServlet, MarksServlet, AttendanceServlet
│       └── util/         → DBConnection.java, ValidationUtil.java
├── WebContent/
│   ├── jsp/              → login, dashboard, addStudent, viewStudents, editStudent,
│   │                        manageCourses, manageMarks, manageAttendance,
│   │                        studentDashboard, myMarks, myAttendance, error
│   └── WEB-INF/
│       ├── web.xml
│       └── lib/          → mysql-connector-j.jar
└── Dockerfile
```

---

## 🚀 Run Locally

### Prerequisites
- Java JDK 11+
- Apache Tomcat 9
- MySQL 5.7+
- Eclipse IDE for Enterprise Java

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/shivrajcodez/CampusConnect.git
```

**2. Import in Eclipse**
- File → Import → Existing Projects into Workspace
- Select the cloned folder

**3. Setup MySQL**
- Create database: `student_management_db`
- Run the SQL script from `database.sql`

**4. Update DB credentials**
- Open `src/com/sms/util/DBConnection.java`
- Update `USERNAME` and `PASSWORD` with your MySQL credentials

**5. Add MySQL JAR**
- Download `mysql-connector-j-8.x.jar`
- Add to `WebContent/WEB-INF/lib/`
- Add to Build Path

**6. Run on Server**
- Right-click project → Run As → Run on Server → Tomcat 9

**7. Open browser**
```
http://localhost:8080/StudentManagementSystem/
```

---

## 🐳 Deploy with Docker
```dockerfile
FROM tomcat:9.0-jdk17-temurin
RUN rm -rf /usr/local/tomcat/webapps/*
COPY StudentManagementSystem.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
```

---

## 📊 Grade System

| Total Marks | Grade |
|-------------|-------|
| 90 - 100    | A+    |
| 80 - 89     | A     |
| 70 - 79     | B     |
| 60 - 69     | C     |
| 50 - 59     | D     |
| Below 50    | F     |

> Internal marks: 0-50 | External marks: 0-50 | Total: 0-100

---

## 🏗️ Architecture

This project follows the **MVC (Model-View-Controller)** pattern:

- **Model** → Java classes in `com.sms.model` (Student, Course, Marks, etc.)
- **View** → JSP pages in `WebContent/jsp/`
- **Controller** → Servlets in `com.sms.servlet`
- **DAO Layer** → Database operations in `com.sms.dao`

---

## 👨‍💻 Developer

**Shivraj** — Third Year Computer Engineering  
SPPU Internship Project — Java Full Stack  

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

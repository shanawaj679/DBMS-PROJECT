Student Management System

A web application for managing students, courses, and enrollments using Node.js, Express, MySQL, and a custom HTML/CSS/JavaScript frontend.

Prerequisites





Node.js (v16 or higher)



MySQL (v8 or higher)



Git

Setup





Clone the repository:

git clone https://github.com/shane/student-management-system.git
cd student-management-system



Install dependencies:

npm install



Set up MySQL database:





Create a database named Studentdata.



Run the following SQL to create tables:

CREATE DATABASE IF NOT EXISTS Studentdata;
USE Studentdata;

CREATE TABLE Students (
    StudentID VARCHAR(36) PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) NOT NULL UNIQUE,
    DateOfBirth DATE NOT NULL,
    Status ENUM('Active', 'Inactive') DEFAULT 'Active'
);

CREATE TABLE Courses (
    CourseID VARCHAR(36) PRIMARY KEY,
    CourseName VARCHAR(100) NOT NULL,
    Credits INT NOT NULL,
    Description TEXT
);

CREATE TABLE Enrollments (
    EnrollmentID VARCHAR(36) PRIMARY KEY,
    StudentID VARCHAR(36),
    CourseID VARCHAR(36),
    EnrollmentDate DATE,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID) ON DELETE CASCADE,
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID) ON DELETE CASCADE
);



Configure environment variables:





Create a .env file in the root directory:

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=Studentdata
PORT=3000



Run the application:





Development mode:

npm run dev



Production mode:

npm start



Access the application: Open http://localhost:3000 in your browser.

Hosting

To host on a platform like Render or Heroku:





Push the repository to GitHub.



Set up a MySQL database on the hosting platform or a service like PlanetScale.



Configure environment variables in the hosting platform's dashboard.



Deploy the application using the platform's Node.js deployment instructions.

License

MIT

# 1. Project Overview and Team Details
#### Project name: Data Analyst Job Market Analysis Application
> Course Information:
Course Name: Object Oriented Programming with Java (ITE23005)
  
Information Student
>
    1. Nguyen Vy Thien Long
       Class 24CVM, Student number: 77482403190
    2. Nguyen Nhan Duc
       Class 24CVM, Student numver: 77482403177
Project Information
>
Dataset Used: company_dim.csv, job_postings_fact.csv, skills_job_dim.csv, skills_dim.csv
GitHub Repository Link (Public): `https://github.com/duck11102006/FinalProject/tree/master`
Brief Project Description: This project looks into the job market for data analysts using 2023 data and explores the types of jobs available, the salary range, the skill requirements for the jobs and the employers posting the jobs.

# 2. Technology and Development Environment
Programming Language: Java (Please install jdk 15 or higher)
Database: SQLYog
Integrated Development Environment (IDE): Eclipse(version 12-2024)
Other Libraries: 
+ JFreeChart `jfreechart-demo-1.5.2-jar-with-dependencies`
+ MySQL Connector `mysql-connector-j-9.3.0`
+ jBCrypt `jbcrypt-0.4.jar`
+ FlatLaf `flatlaf-3.6.jar`

# 3.  Installation and Configuration Guide
### Prerequisites
JDK 15 or higher
SQLYog for SQL Queries
DBeaver for create and import data sql
IDE: eclipse
### Database Installation Guide
This section outlines the steps to set up the SQL database required for the project.
In SQLYog, first, you need to create a new query.
Then, copy the following code to create the necessary tables.
>CREATE DATABASE sql_corse;
USE sql_corse;
CREATE TABLE company_dim (
    company_id INT PRIMARY KEY,
    NAME TEXT,
    link TEXT,
    link_google TEXT,
    thumbnail TEXT
);
CREATE TABLE skills_dim (
    skill_id INT PRIMARY KEY,
    skills TEXT,
    TYPE TEXT
);
CREATE TABLE job_postings_fact (
    job_id INT PRIMARY KEY,
    company_id INT,
    job_title_short VARCHAR(255),
    job_title TEXT,
    job_location TEXT,
    job_via TEXT,
    job_schedule_type TEXT,
    job_work_from_home TINYINT(1),
    search_location TEXT,
    job_posted_date DATETIME,
    job_no_degree_mention TINYINT(1),
    job_health_insurance TINYINT(1),
    job_country TEXT,
    salary_rate TEXT,
    salary_year_avg DECIMAL(10,2),
    salary_hour_avg DECIMAL(10,2),
    FOREIGN KEY (company_id) REFERENCES company_dim(company_id)
);
CREATE TABLE skills_job_dim (
    job_id INT,
    skill_id INT,
    PRIMARY KEY (job_id, skill_id),
    FOREIGN KEY (job_id) REFERENCES job_postings_fact(job_id),
    FOREIGN KEY (skill_id) REFERENCES skills_dim(skill_id)
);
CREATE TABLE users (
    username VARCHAR(50) PRIMARY KEY,
    PASSWORD VARCHAR(255) NOT NULL
    email VARCHAR(100)
);
-- Indexes
CREATE INDEX idx_company_id ON job_postings_fact(company_id);
CREATE INDEX idx_skill_id ON skills_job_dim(skill_id);
CREATE INDEX idx_job_id ON skills_job_dim(job_id);

Connecting to the Database using DBeaver
Next, in DBeaver, navigate to the taskbar. Select Database, then choose New Database Connection, and search for MySQL to establish a connection. Once the connection is successful, you'll need to accurately enter the username, password, and port details from the SQLYog database you've set up previously.

If you've followed the steps correctly, after the database creation is complete, you'll see it listed. Click on the database section, and you'll find the tables you created previously.

Next, right-click on each table individually and select "Import Data" to import the corresponding dataset. This step might take some time as the dataset is quite large.

After the import process is complete, return to SQLYog, refresh the database view, and view the tables to confirm that the data has been successfully loaded. If the data is displayed, your SQL setup is complete.

### Java Project Configuration Guide
1. Obtain the Source Code from github
2. Import the Source Code file into project by clicking on the file in the taskbar then click Open Projects From File System and find the downloaded Source on github
# 4. Running the Application
To run the application from the Eclipse IDE, navigate to the `AppMain.java` class and execute it as a Java Application.

# 5. Project Directory Structure 
1. The `src` Directory (Source Code)
Purpose: The `src` directory serves as the central repository for all the project's source code, primarily written in Java. It is further organized into specific packages, each corresponding to distinct classes and functionalities within the application.
2. The `lib` Directory
Purpose: The `lib` directory is designated to store all external libraries (JAR files) required by the project.

    Important Note: These libraries must be imported into your Integrated Development Environment (IDE) for the project to compile and run correctly. Simply having them in the lib folder without importing them into the IDE's build path will not suffice.
3. The `bin` Directory (Binary Output)
Purpose: The `bin` directory, short for "binary," serves as the output folder where compiled files from the source code in the src directory are stored. For Java projects, these are typically Java bytecode files with the .class extension.

Important Note: Please verify that the images directory is present within the `bin` folder, as this is the designated path for image files used by the application.








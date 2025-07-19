# 🎓 Educational Management Platform (Intranet)

A full-stack project for an educational intranet, designed to centralize academic management and facilitate communication between administrators, teachers, and students. The platform is deployed on the AWS cloud to ensure scalability and availability.

---

## 🚀 Architecture and AWS Deployment

This project is fully deployed on Amazon Web Services, using a decoupled and scalable architecture:

-   **Frontend (React JS):** Deployed as a static website on **AWS S3** for fast, low-cost content delivery.
-   **Backend (Spring Boot):** Hosted on an **AWS EC2** instance, providing the necessary computing power for the business logic.
-   **Database (SQL Server):** Managed via **AWS RDS**, ensuring high availability, automatic backups, and security.

---

## 🧠 Core Features

The platform offers different panels and functionalities depending on the user's role.

### 👨‍💼 Administrator

-   **Complete Student Management:** Add, delete, and edit student information. Includes filters by name, ID, grade, and section for quick searches.
-   **Academic Management:** Create courses and sub-courses, and assign them to the appropriate teachers based on their specialty.
-   **Report Generation:** Generate and download grade reports (per unit or bimonthly) in **Excel** format. The file format is compliant with required national standards.
-   **Universal Access:** Can access and modify any data in the system if necessary.

### 👨‍🏫 Teacher

-   **Restricted Access:** Views only the courses and students assigned to them based on their specialty.
-   **Grade Entry:** Enters student grades for each unit. The system automatically calculates bimonthly averages (every 2 units) and the final course average.
-   **Student Rosters:** Accesses student lists organized by grade and section for their courses.
-   **Profile Management:** Can edit their primary personal information.

### 🎓 Student

-   **Academic Information:** View assigned courses, the teacher in charge of each, schedules, and assignments.
-   **Grade Tracking:** Review detailed grades by unit and bimester.
-   **Honor Roll:** Access a ranking of the institution's top-performing students.
-   **Virtual Assistant (Beta):** Interact with a chatbot to get general information about the institution.
-   **Profile Management:** Can view their data and edit their password. The system includes a security alert reminding them to change their initial password (which is their ID by default).

---

## ⚙️ Technologies Used

### 🔧 Backend

-   **Framework:** Spring Boot
-   **Language:** Java
-   **Security:** Spring Security + JWT (JSON Web Tokens)
-   **Data Access:** Spring Data JPA / Hibernate
-   **Database:** SQL Server
-   **Reports:** Apache POI (for Excel file generation)
-   **Cloud:** AWS SDK for Java

### 🎨 Frontend

-   **Library:** React JS + Vite
-   **Styling:** Pure CSS (no frameworks)

---

## 🌐 Local Installation and Setup

Follow these steps to run the project in a development environment.

### **Prerequisites**

-   Java JDK 17 or higher
-   Maven
-   Node.js and npm
-   SQL Server

### **1. Database (SQL Server)**

1.  Ensure you have an active instance of SQL Server.
2.  Create a database named `BDCOLEGIO`.
3.  The system will use JPA (`ddl-auto=update`) to generate the tables, but if you have a creation script, run it here.

### **2. Backend Setup (Spring Boot)**

1.  Navigate to the `backend/` folder.
2.  Open the `src/main/resources/application.properties` file and update it with your local and AWS credentials.

    ```properties
    spring.application.name=Integrador_Backend

    # ====== LOCAL DEVELOPMENT Configuration ======
    spring.datasource.url=jdbc:sqlserver://localhost:1433;instanceName=SQLEXPRESS;databaseName=BDCOLEGIO;TrustServerCertificate=true;
    spring.datasource.username=sa
    spring.datasource.password=12345

    # ====== JPA Configuration ======
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.SQLServerDialect

    # ====== JWT Configuration ======
    security.jwt.key.private=964ffdb5e95797ad2be8a036924d97a1df90a004b69e25093959be7d5104601b
    security.jwt.user.generator=AUTH0JWT-BACKEND-USER
    security.jwt.key.refresh=AUTH0JWT-BACKEND-USER-refresh

    # ====== AWS DEPLOYMENT Configuration ======
    # Note: For EC2 deployment, it is recommended to use IAM roles instead of hardcoded keys.
    aws.accessKeyId=[ENTER YOUR AWS ACCESS KEY]
    aws.secretKey=[ENTER YOUR AWS SECRET KEY]
    aws.s3.bucketName=[ENTER YOUR S3 BUCKET NAME]
    aws.s3.region=[ENTER YOUR BUCKET REGION]
    ```
3.  Run the application:
    ```bash
    mvn spring-boot:run
    ```

### **3. Frontend Setup (React)**

1.  Open another terminal and navigate to the `frontend/` folder.
2.  Install the dependencies:
    ```bash
    npm install
    ```
3.  Start the development server:
    ```bash
    npm run dev
    ```
    The application will be available at `http://localhost:5173` (or the port shown by Vite).

---

If you have any problems, please contact the author.

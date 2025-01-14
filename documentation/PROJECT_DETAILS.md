# Project Details

# Table of Contents
- [Project Description](#project-description)
- [Functional Requirements](#functional-requirements)
- [Non-functional Requirements](#non-functional-requirements)
- [Database Diagram](#database-diagram)
- [JSON Input & Output for RESTful endpoints](#json-input-and-output-for-restful-endpoints)
- [Project Checklist](#project-checklist)
- [Project File Structure](#project-file-structure)

## Project Description

Workout-logger is a web application designed to help users set fitness goals, input their workouts in real-time, and keep a history of all their workouts. This application will implement a three-tier architecture which includes the client, server, and database. 

## Functional Requirements

- **User Registration:** Allow users to sign up with email and password.
- **User Login:** Allow users to log in securely with their credentials.
- **Profile Management:** Allow users to update personal information, such as name, email, and profile picture.
- **Password Management:** Provide functionality to reset or change passwords.
- **Workout Entry:** Allow users to log workouts with details like:
   - Date
   - Workout name
   - Workout type
- **Workout History:** Enable users to view their workout history in a chronological list.
- **Data Editing:** Provide the ability to edit or delete logged workouts.
- **Graphs:** Visualize progress toward goals using numeric data.
- **Exercise Entry:** Allow users to log exercises, **within Workout Entry**, with details like:
  - Exercise name
  - Sets, reps, and weight
- **Goal Setting:** Enable users to set goals.
- **User Management:** Allow administrators to view, edit, or delete user accounts if needed.
- **Exercise Management:** Allow administrators to manage the default exercise database, including adding, updating, or removing entries.
- **Secure Authentication:** Implement secure methods like OAuth and JWT for user authentication.

## Non-functional Requirements
- **Response Time:** All user interactions, such as viewing workout logs or submitting a new workout entry, should have a response time of under 2 seconds.
- **Scalability:** The application should handle increased user traffic without significant performance degradation.
- **Data Handling:** The system should efficiently manage and query large datasets of workout logs.
- **User Interface:** Provide an intuitive and visually appealing interface optimized for both beginners and advanced users.
- **Cross-Platform Support:** The application should function seamlesslly across different devices (desktop, tablet, and mobile) and browsers.
- **Code Quality:** Adhere to coding standards and best practices to ensure code readability and maintainability.
- **Modular Design:** Structure the system into loosely coupled, highly cohesive modules for easier updates and debugging.
- **Documentation:** Maintain comprehensive documentation for developers (e.g., API docs) and users (e.g., FAQs, help guides).
- **Vertical and Horizontal Scaling:** Design the system to scale efficiently by adding resources or new instances.

## Database Diagram

## JSON Input and Output for RESTful endpoints

1. Register User
  - Endpoint: `POST /api/users/register`
  - Input:
    ```json
    {
       "first_name": "John",
       "last_name": "Doe",
       "user_name": "johndoe",
       "email": "johndow@example.com",
       "password": "securepassword123",
       "created_at": "2025-01-15T00:00:00Z"
    }
    ```
  - Output:
    ```json
    {
       "message": "User registered successfully",
       "userId": 1
    }
    ```

2. Login
  - Endpoint: `POST /api/users/login`
  - Input:
    ```json
      {
        "email": "johndoe@example.com",
        "password": "securepassword123"
      }
    ```
  - Output:
    ```json
      {
        "token": "jwt-token-string",
        "userId": 1
      }
    ```

3. Update Profile
   - Endpoint: `PUT /api/users/{userId}`
   - Input:
     ```json
      {
        "name": "John D.",
        "profilePicture": "base64-encoded-image"
      }
     ```
  - Output:
    ```json
      {
        "message": "Profile updated successfully"
      }
    ```

4. Log Workout
   - Endpoint: `POST /api/workouts`
   - Input:
     ```json
      {
        "userId": 1,
        "date": "2025-01-05",
        "notes": "Leg day workout"
      }
     ```
   - Output:
     ```json
      {
        "message": "Workout logged successfully",
        "workoutId": 10
      }
     ```

5. Edit Workout
   - Endpoint: `PUT /api/workouts/{workoutId}`
   - Input:
     ```json
      {
        "workout_id": "1",
        "notes": "Updated notes for leg day workout"
      }
     ```
   - Output:
     ```json
     ```

5. Edit Workout
   - Endpoint: ``
   - Input:
     ```json
     ```
   - Output:
     ```json
     ```

## Project Checklist

### 1. Create the UI/UX Design using Figma

#### Design the User Interface (UI):
- [ ] Create wireframes for each page of your workout tracker app, such as:
  - [ ] Home Page (login/signup forms, workout dashboard).
  - [ ] Workout Log Page (view and create new workouts).
  - [ ] Progress Analytics Page (charts and graphs for tracking).
- [ ] Use Figma to design each component, focusing on:
  - Color Scheme
  - Typography (simple and readable fonts)
  - Layout (user-friendly, intuitive navigation)
  - Responsiveness (ensure the design adapts to different screen sizes)
- [ ] Design Interactive Prototypes:
  - Create clickable prototypes to simulate the user flow and interaction between pages.
  - Test the flow with potential users or teammates for feedback.
  - Ensure that the design has an intuitive experience with clear aactions (e.g., buttons, navigation).
- [ ] Export Assets
  - Export icons, images, and other assets needed for your frontend development.

### 2. Initialize the Project Structure

#### Frontend:
- [ ] Create a Next.js project:
  ```bash
  npx create-next-app@latest workout-logger-frontend --typescript
  ```
- [ ] Set up the folder structure (e.g., components, pages, styles).
- [ ] Commit the initial setup to your repository

#### Backend:
- [ ] Use Spring Initializr to create your Spring Boot project with dependencies for:
  - Spring Web (for REST APIs)
  - Spring Data JPA (for database interaction)
  - PostgreSQL Driver
  - Spring Security (for authentication/authorization)
- [ ] Commit the backend project structure to your repository

### 3.  Design the Database Schema

- [ ] Define the tables for your workout tracker:
  - Example tables:
    1. `users` (id, name, email, hashed_password)
    2. `workouts` (id, user_id, date, type, duration)
    3. `exercises` (id, workout_id, name, sets, reps, weight)
  - Use an ERD tool like dbdiagram.io to visualize your schema
- [ ] Configure your PostgreSQL database on RDS and connect it to the Spring Boot backend.

### 4. Set Up AWS Infrastructure

- Infrastructure as Code:
  - [ ] Use **Boto3** to script the creation of:
    - [ ] EC2 instances for the backend.
    - [ ] RDS PostgreSQL database.
    - [ ] Load balancers and auto-scaling groups.
  - [ ] Set up your AWS Lambda function environment for serverless tasks (e.g., scheduled job for weekly summaries).
 
### 5. Build the Frontend UI

- [ ] Implement the frontend UI using Figma designs as the reference:
  - [ ] Design key pages for the app:
    - [ ] User authentication (login/sign-up).
    - [ ] Dashboard to view workout logs.
    - [ ] Form to log new workouts and exercises.
    - [ ] Analytics (charts/graphs for progress tracking).
- [ ] Implement responsive design based on Figma's mobile/tablet/desktop mockups.

### 6. Build Backend REST APIs

- [ ] Create endpoints for:
  - [ ] User registration and login.
  - [ ] CRUD opperations for workouts and exercises.
  - [ ] Fetching user-specific analytics.
- [ ] Test APIs using **Postman** or **cURL**.

### 7. Integrate Frontend and Backend

- [ ] Set up API routes in Next.js to communicate with the backend.
- [ ] Use **Axios** or **Fetch API** to make HTTP requests.
- [ ] Ensure secure communication using **JWT authentication**.

### 8. Add CI/CD Pipelines

- [ ] Use **GitHub Actions** to automate:
  - Linting and testing on pull requests.
  - Deployment to AWS.

### 9. Implement Scalable Features

- [ ] Add auto-scaling groups for the EC2 backend to handle high traffic.
- [ ] Configure a load balancer (e.g., AWS Elastic Load Balancer) to distribute traffic.

### 10. Test and Optimize

- [ ] Conduct end-to-end testing (frontend to backend to database).
- [ ] Load test your backend using tools like **JMeter** or **k6**.
- [ ] Optimize database queries and API responses.

### 11. Deploy

- [ ] Deploy the backend on **EC2** and **RDS**.
- [ ] Deploy the frontend on **AWS Amplify** or **S3 + CloudFront** for scalability.
- [ ] Use **AWS Lambda** for serverless functions.

### 12. Monitor and Maintain

- [ ] Set up monitoring for your services:
  - [ ] Use **Amazon CloudWatch** for logs and metrics.
  - [ ] Configure alerts for potential issues (e.g., high CPU usage, database connections).

## Project File Structure

```bash
workout-logger/
├── frontend/                      # Frontend (Vite + JavaScript)
│   ├── src/                       # Source code
│   │   ├── components/            # React components
│   │   ├── pages/                 # Page components (if routing is used)
│   │   ├── assets/                # Static assets like images and fonts
│   │   ├── App.jsx                # Main app entry point
│   │   └── main.jsx               # Main JavaScript entry point
│   ├── public/                    # Static assets (served as-is)
│   ├── index.html                 # HTML template for the app
│   ├── vite.config.js             # Vite configuration file
│   ├── package.json               # Dependencies for the frontend
│   ├── .eslintrc.js               # Linting configuration
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Frontend-specific documentation
├── backend/                       # Backend (Spring Boot)
│   ├── src/                       # Source code for Spring Boot
│   │   ├── main/
│   │   │   ├── java/
│   │   │   └── resources/
│   │   └── test/
│   ├── pom.xml                    # Maven/Gradle dependencies
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Backend-specific documentation
├── serverless/                    # Serverless functions (AWS Lambda in Python)
│   ├── functions/                 # Individual Lambda functions
│   ├── requirements.txt           # Python dependencies
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Serverless-specific documentation
├── infrastructure/                # Infrastructure as code (Python with Boto3)
│   ├── scripts/                   # Scripts for resource provisioning
│   ├── requirements.txt           # Python dependencies
│   ├── .gitignore                 # Git ignore file
│   └── README.md                  # Infrastructure-specific documentation
├── database/                      # Database-related files
│   ├── migrations/                # SQL or migration scripts
│   ├── schema.sql                 # Initial database schema
│   └── README.md                  # Database-specific documentation
├── .github/                       # GitHub-specific configurations
│   ├── workflows/                 # GitHub Actions workflows for CI/CD
├── docs/                          # Project documentation
│   ├── architecture.md            # Architecture overview
│   ├── requirements.md            # Requirements document
│   └── README.md                  # General documentation
├── .gitignore                     # Root Git ignore file
├── LICENSE                        # License file
├── README.md                      # Main project README
└── CONTRIBUTING.md                # Contribution guidelines
```

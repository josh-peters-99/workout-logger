# Project Details

## Project Description

Workout-logger is a web application designed to help users set fitness goals. They can set goals for building strength, reaching a certain duration in cardio, or gaining/losing weight.Users will input their workouts in real-time, and a history will be kept of all their workouts. This application will implement a three-tier architecture which includes the client, server, and database.

## Example Users/Persona's
<details>
   <summary>Persona 1: Dedicated Fitness Enthusiast</summary>
   <ul>
      <li>Name: Alex Johnson</li>
      <li>Age: 28</li>
      <li>Occupation: Persoanl Trainer</li>
      <li>Fitness Goals: Build muscle and increase strength</li>
      <li>Behavior:</li>
      <ul>
         <li>Works out 5-6 times per week, often combining strength training and cardio.</li>
         <li>Tracks progress meticulously and looks for trends over weeks/months.</li>
         <li>Enjoys setting personal records (e.g., bench press, squat, deadlift).</li>
         <li>Frequently explores workout programs and adjusts routines based on progress.</li>
      </ul>
      <li>Pain Points:</li>
      <ul>
         <li>Frustrated by cluttered fitness tracking apps that lack real-time input features.</li>
         <li>Finds it hard to visualize long-term progress or view trends in workout history.</li>
      </ul>
      <li>Needs from Workout-Logger:</li>
      <ul>
         <li>A clean, intuitive UI for quickly logging workouts during or after gym sessions.</li>
         <li>Advanced analytics to track progress against goals (e.g., lifting heavier weights over time).</li>
      </ul>
   </ul>
</details>

<details>
   <summary>Persona 2: New Year's Resolution Beginner</summary>
   <ul>
      <li>Name: Jamie Carter</li>
      <li>Age: 35</li>
      <li>Occupation: Teacher</li>
      <li>Fitness Goals: Lose 15 pounds and improve overall health</li>
      <li>Behavior:</li>
      <ul>
         <li>Works out 2–3 times a week, primarily doing bodyweight exercises and light cardio.</li>
         <li>Prefers accessible features with minimal setup.</li>
         <li>Wants a visual representation of self-improvement over time.</li>
         <li>Frequently explores workout programs and adjusts routines based on progress.</li>
      </ul>
      <li>Pain Points:</li>
      <ul>
         <li>Overwhelmed by overly complex fitness apps with unnecessary features.</li>
         <li>Struggles to stay motivated without regular feedback or achievements.</li>
      </ul>
      <li>Needs from Workout-Logger:</li>
      <ul>
         <li>Simple goal-setting and real-time workout tracking.</li>
         <li>Encouragement through badges or small achievements (e.g., streaks, milestones).</li>
      </ul>
   </ul>
</details>

## Requirements
<details>
   <summary>Functional Requirements</summary>
   <br>
   <ul>
      <li>User Registration: Allow users to sign up with email and password.</li>
      <li>User Registration: Allow users to sign up with email and password.</li>
      <li>User Login: Allow users to log in securely with their credentials.</li>
      <li>Profile Management: Allow users to update personal information, such as name, email, and profile picture.</li>
      <li>Password Management: Provide functionality to reset or change passwords.</li>
      <li>Workout Entry: Allow users to log workouts with details like:</li>
         <ul>
            <li>Date</li>
            <li>Workout name</li>
            <li>Workout type</li>
         </ul>
      <li>Workout History: Allow users to access a log of their workout history.</li>
      <li>Data Editing: Provide the ability to edit or delete logged workouts.</li>
      <li>Graphs: Visualize progress toward goals using numeric data.</li>
      <li>Exercise Entry: Allow users to log exercises, within Workout Entry, with details like:</li>
         <ul>
            <li>Exercise name</li>
            <li>Sets, reps, and weight</li>
         </ul>
      <li>Goal Setting: Enable users to set goals.</li>
      <li>User Management: Allow administrators to view, edit, or delete user accounts if needed.</li>
      <li>Exercise Management: Allow administrators to manage the default exercise database, including adding, updating, or removing entries.</li>
      <li>Secure Authentication: Implement secure methods like OAuth and JWT for user authentication.</li>
   </ul>
</details>

<details>
   <summary>Non-Functional Requirements</summary>
   <br>
   <ul>
      <li>Response Time: All user interactions, such as viewing workout logs or submitting a new workout entry, should have a response time of under 2 seconds.</li>
      <li>Scalability: The application should handle increased user traffic without significant performance degradation.</li>
      <li>Data Handling: The system should efficiently manage and query large datasets of workout logs.</li>
      <li>User Interface: Provide an intuitive and visually appealing interface optimized for both beginners and advanced users.</li>
      <li>Cross-Platform Support: The application should function seamlesslly across different devices (desktop, tablet, and mobile) and browsers.</li>
      <li>Code Quality: Adhere to coding standards and best practices to ensure code readability and maintainability.</li>
      <li>Modular Design: Structure the system into loosely coupled, highly cohesive modules for easier updates and debugging.</li>
      <li>Documentation: Maintain comprehensive documentation for developers (e.g., API docs) and users (e.g., FAQs, help guides).</li>
      <li>Vertical and Horizontal Scaling: Design the system to scale efficiently by adding resources or new instances.</li>
   </ul>
</details>

## Database Tables

### User Table

| Attribute Name | Data Type | Description                               |
|----------------|-----------|-------------------------------------------|
| user_id        | String    | Unique identifier for the user            |
| name           | String    | User's name                               |
| email          | String    | User's email                              |
| password       | String    | User's password                           |
| height         | Integer   | User's height                             |
| weight         | Integer   | User's weight                             |
| workout_ids    | List      | Array of workout IDs associated with the user |

### Workout Table

| Attribute Name | Data Type | Description                               |
|----------------|-----------|-------------------------------------------|
| workout_id     | String    | Unique identifier for the workout         |
| workout_name   | String    | Workout's name                            |
| workout_date   | String    | Date of the workout in ISO 8601 format    |
| exercise_ids   | List      | Array of exercises IDs associated with the workout |

### Exercise Table

| Attribute Name | Data Type | Description                                     |
|----------------------|-----------|-------------------------------------------|
| exercise_id          | String    | Unique identifier for the exercise        |
| exercise_category    | String    | Exercise category (strength or cardio)    |
| exercise_subcategory | String    | Subcategory of exercise                   |
| set_ids              | List      | Array of set IDs associated with the exercise |

### Set Table

| Attribute Name | Data Type | Description                                     |
|----------------------|-----------|-------------------------------------------|
| set_id               | String    | Unique identifier for the set             |
| set_category         | String    | Set category (numeric or timed)           |
| set_count            | Number    | Counter of sets                           |
| reps                 | Number    | Number of reps                            |
| weight               | Number    | Weight used for set                       |
| duration             | Number    | Duration of the set in seconds            |

## JSON Input and Output for RESTful endpoints

<details>
<summary>Register User</summary>

### Endpoint:
`POST /api/users/register`

### Input:

```json
{
   "user_id": "123",
   "first_name": "John",
   "last_name": "Doe",
   "user_name": "johndoe",
   "email": "johndoe@example.com",
   "password": "securepassword123",
   "height": "6'2",
   "weight": "190",
   "created_at": "2025-01-15T00:00:00Z"
}
```

### Output:
```json
{
   "message": "User registered successfully",
   "user_id": "123"
}
```
</details>

<details>
<summary>Login</summary>

### Endpoint:
`POST /api/users/login`

### Input:

```json
  {
    "email": "johndoe@example.com",
    "password": "securepassword123"
  }
```

### Output:
```json
  {
    "token": "jwt-token-string",
    "user_id": "123"
  }
```
</details>

<details>
<summary>Update Profile</summary>

### Endpoint:
`PUT /api/users/{user_id}`

### Input:

```json
 {
   "user_id": "123",
   "weight": "195"
 }
```

### Output:
```json
  {
    "message": "Profile updated successfully"
  }
```
</details>

<details>
<summary>Log Workout</summary>

### Endpoint:
`POST /api/workouts`

### Input:

```json
 {
   "user_id": "123",
   "workout_id": "456",
   "workout_name": "Push Day",
   "workout_category": "strength",
   "workout_subcategory": "push",
   "created_at": "2025-01-05"
 }
```

### Output:
```json
 {
   "message": "Workout logged successfully",
   "workout_id": "456"
 }
```
</details>

<details>
<summary>Create Goal</summary>

### Endpoint:
`POST /api/goals`

### Input:

```json
 {
   "user_id": "123",
   "goal_category": "strength",
   "goal_subcategory": "push",
   
 }
```

### Output:
```json
 {
   "message": "Workout logged successfully",
   "workoutId": 10
 }
```
</details>

## Architectural Stack
- Frontend: **Vite (JavaScript)** hosted using **Amplifiy**
- Backend: **Java (Spring Boot)** with REST APIs
- Database: **DynamoDB** with free tier for my database
- Serverless: **AWS Lambda** and **API Gateway**
- Automate deployment for both environments (beta and production) using CI/CD pipelines with **AWS CodePipeline** (free tier available).

## Test Plan

<details>
   <summary>White Box Tests</summary>
   <ul>
      <li>Client-Side (Frontend)</li>
      <ul>
         <li>Input Validation: Ensure workout input forms handle valid and invalid inputs appropriately.</li>
         <li>UI Logic: Verify that UI components update dynamically based on user actions.</li>
         <li>Local Storage/State Management: Test that user preferences are correctly saved and retrieved.</li>
      </ul>
      <li>Server-Side (Backend)</li>
      <ul>
         <li>Authentication Logic: Test login and session handling for proper authentication flow.</li>
         <li>Data Handling: Verify API endpoints correctly process and store workout data.</li>
         <li>Edge Cases: Ensure the server handles edge cases like large payloads and special characters.</li>
         <li>Database Interactions: Test database queries for correct data storage and retrieval.</li>
      </ul>
   </ul>
</details>

<details>
   <summary>Black Box Tests</summary>
      <ul>
      <li>Functional Tests</li>
      <ul>
         <li>Workout Logging: Confirm workouts are logged and displayed accurately.</li>
         <li>Goal Setting: Test creating, updating, and deleting fitness goals.</li>
         <li>Progress Tracking: Verify progress displays are accurate based on input data.</li>
      </ul>
      <li>Performance Tests</li>
         <ul>
            <li>API Response Times: Measure server response times under different loads.</li>
            <li>Database Performance: Test database performance for large datasets and queries.</li>
            <li>Scalability: Simulate multiple users to ensure system stability under load.</li>
         </ul>
      <li>Integration Tests>
         <ul>
            <li>End-to-End Workflow: Test the full user journey from goal setting to progress tracking.</li>
            <li>Third-Party Tools: Verify integrations with external tools and APIs.</li>
         </ul>
      <li>Security Tests>
         <ul>
            <li>Input Validation: Ensure the app handles invalid or malicious inputs securely.</li>
            <li>Authentication: Verify session expiration and unauthorized action handling.</li>
         </ul>
      <li>Usability Tests</li>
      <ul>
         <li>Error Messages: Check that error messages appear for invalid inputs or failures.</li>
      </ul>
   </ul>
</details>

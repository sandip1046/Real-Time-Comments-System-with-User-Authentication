# Real-Time Comments System

This project is a real-time comments application built with Next.js for the frontend and Node.js with TypeScript for the backend. It uses MySQL for data storage, Material UI (MUI) for styling, and Socket.IO for real-time comment updates.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Installation](#installation)
  - [Frontend Setup](#frontend-setup)
  - [Backend Setup](#backend-setup)
  - [Database Setup](#database-setup)
- [Running the App](#running-the-app)
- [Assumptions](#assumptions)

## Features

- User Authentication
- Real-time Comment Posting and Updates using Socket.IO
- Comments stored in MySQL
- Frontend styled with Material UI (MUI)

## Tech Stack

- **Frontend**: Next.js, Material UI (MUI), Axios
- **Backend**: Node.js, Express, TypeScript, Socket.IO
- **Database**: MySQL

## Getting Started

To get a local copy up and running, follow these steps:

### Clone the repository:

```bash
git clone https://github.com/your-username/real-time-comments.git
cd real-time-comments
```
This project has two main folders:

- **frontend**: Contains the Next.js application.
- **backend**: Contains the Node.js API and real-time server logic.


## Installation

  ### Frontend Setup
  
  1. Navigate to the frontend directory:
  
     ```bash
     cd frontend
     ```
  2. Install the required dependencies:
  
    ```bash
    npm install
    ```
  3. Start the development server:
  
    ```bash
    npm run dev
    ```
  By default, the frontend will run on http://localhost:3000.
  
  ### Backend Setup
  
  1. Open a new terminal and navigate to the backend directory:
  
         ```bash
         cd backend
         ```
  2. Install the required dependencies:
  
          ```bash
          npm install
          ```
  3. Configure environment variables:
      Create a .env file in the backend folder with the following contents
     
    ```bash
    DB_HOST=localhost
    DB_USER=root
    DB_PASSWORD=yourpassword
    DB_NAME=comments_database
    JWT_SECRET=your_jwt_secret
    ```
  3. Start the backend server:
     
    ```bash
    # Using nodemon
    npx nodemon src/index.ts
    # Or directly with Node.js
    node src/index.ts
    ```
  The backend will run on http://localhost:8000 by default.


  ### Database Setup
  
  1. Install MySQL: Ensure you have MySQL installed and running on your machine.
     
  2. Create a MySQL Database:
       - Log in to MySQL
       - Create the database and tables:
         
             ```bash
                  CREATE DATABASE IF NOT EXISTS comments_database;
                  USE comments_database;
                  CREATE TABLE IF NOT EXISTS users (
                    id INT AUTO_INCREMENT PRIMARY KEY,
                    username VARCHAR(255) NOT NULL,
                    password VARCHAR(255) NOT NULL
                  );
                  CREATE TABLE IF NOT EXISTS comments (
                    id INT AUTO_INCREMENT PRIMARY KEY,
                    user_id INT NOT NULL,
                    comment TEXT NOT NULL,
                    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP,
                    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
                  );
              ```
  3. Update your .env file in the backend directory with the correct database credentials.
  4. Test the Connection: Start the backend server to verify that MySQL is connected without any errors.
  
  By default, the frontend will run on http://localhost:3000.
  
##Running the App

  **Frontend**: 
  
        ```bash
            cd frontend
            npm install
            npm run dev
        ```
  
  **Backend**: 
  
        ```bash
            cd backend
            npm install
            npx nodemon src/index.ts
        ```

##Assumptions

- This setup assumes you have MySQL installed and accessible on your local machine.
- The .env file must be configured with valid MySQL credentials and a JWT secret.

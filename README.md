# Clinic Appointment Backend

A simple Node.js backend using Express and MySQL for handling clinic appointment bookings and contact messages.

## Features

- **Book Appointments:** REST API to book clinic appointments.
- **Contact Form:** REST API to submit contact messages.
- **MySQL Integration:** Stores appointments and contact messages in a MySQL database.

## Prerequisites

- [Node.js](https://nodejs.org/) (v12+ recommended)
- [MySQL Server](https://www.mysql.com/)

## Setup

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd <project-directory>
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Database

Ensure you have a MySQL database named `clinic` and the following tables:

```sql
CREATE DATABASE IF NOT EXISTS clinic;

USE clinic;

CREATE TABLE IF NOT EXISTS bookappointments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(20),
    service VARCHAR(100),
    date DATE,
    message TEXT
);

CREATE TABLE IF NOT EXISTS contacts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    message TEXT
);
```

Update the database credentials in `server.js` if needed:

```js
const db = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "123456", // Change this if your MySQL password is different
  database: "clinic"
});
```

### 4. Start the Server

```bash
node server.js
```

The server will run on [http://localhost:5000](http://localhost:5000).

## API Endpoints

### Book an Appointment

- **POST** `/api/appointments`
- **Body:**
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "1234567890",
    "service": "Dental",
    "date": "2025-06-25",
    "message": "Looking forward to my appointment."
  }
  ```
- **Response:**  
  - `200 OK` on success  
  - `500 Internal Server Error` on failure

### Send Contact Message

- **POST** `/api/contacts`
- **Body:**
  ```json
  {
    "name": "Jane Doe",
    "email": "jane@example.com",
    "message": "I have a question about your services."
  }
  ```
- **Response:**  
  - `200 OK` on success  
  - `500 Internal Server Error` on failure

## Notes

- CORS is enabled for all origins.
- Make sure your MySQL server is running before starting the Node.js server.

## License

MIT

# Doctor Booking System - Backend

This is the backend for the Doctor Booking System, built with Node.js, Express, and MongoDB. It provides a robust API for managing users, doctors, appointments, and administrative tasks.

## Table of Contents

- [About The Project](#about-the-project)
- [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
  - [Admin API](#admin-api)
  - [Doctor API](#doctor-api)
  - [User API](#user-api)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## About The Project

The Doctor Booking System backend facilitates the core functionalities of a doctor appointment management application. It handles user authentication, doctor registration, appointment scheduling, payment processing, and administrative oversight.

## Built With

*   Node.js
*   Express.js
*   MongoDB (Mongoose)
*   CORS
*   Dotenv
*   Multer (for file uploads)
*   Cloudinary (for image storage)
*   Stripe (for payment processing)
*   Nodemon (for development)
*   Bcrypt (for password hashing)
*   JSON Web Token (for authentication)

## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

*   Node.js (LTS version recommended)
*   npm (Node Package Manager)
*   MongoDB instance (local or cloud-based like MongoDB Atlas)
*   Cloudinary account
*   Stripe account

### Installation

1.  Clone the repository:
    ```bash
    git clone <repository-url>
    ```
2.  Navigate to the backend directory:
    ```bash
    cd doctor-booking-system/backend
    ```
3.  Install NPM packages:
    ```bash
    npm install
    ```
4.  Create a `.env` file in the `backend` directory and add the following environment variables:
    ```
    PORT=4000
    MONGODB_URL=<Your MongoDB Connection String>
    CLOUDINARY_CLOUD_NAME=<Your Cloudinary Cloud Name>
    CLOUDINARY_API_KEY=<Your Cloudinary API Key>
    CLOUDINARY_API_SECRET=<Your Cloudinary API Secret>
    STRIPE_SECRET_KEY=<Your Stripe Secret Key>
    JWT_SECRET=<A strong secret key for JWT>
    ```

## Usage

To start the backend server:

```bash
npm start
```

The server will run on the port specified in your `.env` file (default: 4000). You can access the API at `http://localhost:4000`.

## API Endpoints

### Admin API

Base URL: `/api/admin`

| Method | Endpoint                 | Description                                   | Authentication | File Upload |
| :----- | :----------------------- | :-------------------------------------------- | :------------- | :---------- |
| `POST` | `/add-doctor`            | Adds a new doctor.                            | Admin          | Image       |
| `POST` | `/login`                 | Admin login.                                  | None           |             |
| `POST` | `/all-doctors`           | Retrieves all doctors.                        | Admin          |             |
| `POST` | `/change-availability`   | Changes a doctor's availability.              | Admin          |             |
| `GET`  | `/appointments`          | Retrieves all appointments for admin.         | Admin          |             |
| `POST` | `/cancel-appointment`    | Cancels an appointment.                       | Admin          |             |
| `GET`  | `/dashboard`             | Retrieves admin dashboard data.               | Admin          |             |

### Doctor API

Base URL: `/api/doctor`

| Method | Endpoint                 | Description                                   | Authentication |
| :----- | :----------------------- | :-------------------------------------------- | :------------- |
| `GET`  | `/list`                  | Retrieves a list of all doctors.              | None           |
| `POST` | `/login`                 | Doctor login.                                 | None           |
| `GET`  | `/appointments`          | Retrieves doctor's appointments.              | Doctor         |
| `POST` | `/complete-appointment`  | Marks an appointment as complete.             | Doctor         |
| `POST` | `/cancel-appointment`    | Cancels an appointment.                       | Doctor         |
| `GET`  | `/dashboard`             | Retrieves doctor dashboard data.              | Doctor         |
| `GET`  | `/profile`               | Retrieves doctor's profile.                   | Doctor         |
| `POST` | `/update-profile`        | Updates doctor's profile.                     | Doctor         |

### User API

Base URL: `/api/user`

| Method | Endpoint                 | Description                                   | Authentication | File Upload |
| :----- | :----------------------- | :-------------------------------------------- | :------------- | :---------- |
| `POST` | `/register`              | User registration.                            | None           |             |
| `POST` | `/login`                 | User login.                                   | None           |             |
| `GET`  | `/get-profile`           | Retrieves user profile.                       | User           |             |
| `POST` | `/update-profile`        | Updates user profile.                         | User           | Image       |
| `POST` | `/book-appointment`      | Books an appointment.                         | User           |             |
| `GET`  | `/appointments`          | Lists user's appointments.                    | User           |             |
| `POST` | `/cancel-appointment`    | Cancels an appointment.                       | User           |             |
| `POST` | `/payment-stripepay`     | Initiates Stripe payment.                     | User           |             |
| `POST` | `/verify-payment`        | Verifies payment.                             | User           |             |

## Project Structure

```
.
├───.gitignore
├───package-lock.json
├───package.json
├───server.js
├───config/
│   ├───cloudinary.js
│   └───mongodb.js
├───controllers/
│   ├───adminController.js
│   ├───doctorController.js
│   └───userController.js
├───middlewares/
│   ├───authAdmin.js
│   ├───authDoctor.js
│   ├───authUser.js
│   └───multer.js
├───models/
│   ├───appointmentModel.js
│   ├───doctorModel.js
│   └───userModel.js
└───routers/
    ├───adminRoute.js
    ├───doctorRoute.js
    └───userRoute.js
```

*   `server.js`: The main entry point of the application, sets up the Express server, middleware, and routes.
*   `config/`: Contains configuration files for database connection (MongoDB) and Cloudinary.
*   `controllers/`: Contains the logic for handling API requests and interacting with the models.
*   `middlewares/`: Contains middleware functions for authentication (admin, doctor, user) and file uploads (Multer).
*   `models/`: Defines the Mongoose schemas for MongoDB collections (Appointment, Doctor, User).
*   `routers/`: Defines the API routes for different entities (admin, doctor, user).

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.

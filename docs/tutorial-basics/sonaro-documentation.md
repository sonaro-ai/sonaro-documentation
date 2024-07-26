---
sidebar_position: 0
---

# Sonaro Vaso3D Documentation

Welcome to the Sonaro Vaso3D documentation! This guide provides an overview of our backend and frontend systems, detailing their functionality, setup, and usage.

## Sonaro Vaso3D Backend API with Async Segmentation API 📂🚀

The Sonaro Vaso3D backend API is designed for efficient and secure processing of ultrasound images, leveraging asynchronous task management and cloud technologies. Here’s a detailed look at its features and setup:

### Key Features

- **Asynchronous Processing**: Utilizes Celery to handle file processing tasks efficiently and asynchronously.
- **Secure File Handling**: Only accepts and delivers files via pre-signed S3 URLs, ensuring secure and controlled file access.
- **Output Generation**: Converts processed ultrasound images into 3D STL files and MP4 videos representing the ultrasound sweep.
- **Cloud Deployment**: Deployed on AWS EC2 using Docker with GPU support for intensive tasks and NGINX for routing and HTTPS.
- **Token Validation**: Routes are protected by JWT tokens from Cognito, ensuring secure access.

### Installation

**Prerequisites**:

- Python 3.10
- Docker and Docker Compose
- NVIDIA Driver with CUDA support

**Docker Setup**:

1. Ensure Docker and Docker Compose are installed on your machine.
2. Build and run Docker containers for local development:

   ```bash
   docker-compose -f docker-compose.yml up --build
   ```

3. For deployment on EC2, use the EC2-specific Docker Compose configuration:

   ```bash
   docker-compose -f docker-compose-ec2.yml up --build
   ```

4. Configure the `.env.docker-ec2` file for production deployment.

**Additional Setup**:

- Install the `pose-regularization` library:

  ```bash
  git clone https://github.com/IFL-CAMP/pose_regularization.git
  cd pose_regularization/python
  python setup.py install
  ```

### Usage

Run the backend API using Docker. Ensure the correct configuration for local development or EC2 deployment as described above. For a detailed API reference, access the Swagger UI at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs).

## Vaso3D Web App 🌐🖥️

The Vaso3D Web App provides a seamless user experience for interacting with the backend system, featuring a modern, React-based frontend. Here’s an overview:

### Key Features

- **Secure Authentication**: Handles user login and authentication via Cognito.
- **Dashboard**: Central hub for managing patient records, uploading files, and viewing results.
- **Patient Management**: Facilitates the addition and management of patient information.
- **File Uploading**: Upload ultrasound files for processing and view the results.
- **Results**: Displays 3D reconstructions and videos of ultrasound sweeps.
- **Admin Page**: Admin interface for managing users and invitations.

### Getting Started

**Prerequisites**:

- Node.js (Install from [nodejs.org](https://nodejs.org/))

**Installation**:

1. Clone the repository:

   ```bash
   git clone https://github.com/sonaro-ai/Vaso3D-web-app.git
   cd Vaso3D-web-app
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Set up environment variables by creating a `.env` file with the following content:

   ```env
   VITE_SONARO_APP_FIREBASE_KEY=___xxx___
   VITE_SONARO_AWS_CLIENT_ID=___xxx___
   VITE_SONARO_AWS_USERPOOL_ID=___xxx___
   VITE_AWS_REGION=___xxx___
   VITE_S3_BUCKET_NAME=___xxx___
   ```

4. Start the development server:

   ```bash
   npm run dev
   ```

**Technology Stack**:

- **React**: For building user interfaces.
- **TypeScript**: Adds type safety to JavaScript.
- **Vite**: Provides a fast development environment.
- **Tailwind CSS**: Offers utility-first CSS for custom designs.
- **React Router**: Manages routing within the app.
- **Axios**: Handles HTTP requests.

### Documentation and Support

Explore our API documentation at the provided Swagger UI link and refer to this guide for detailed instructions on setup and usage. For any issues or further assistance, please reach out to our team or visit our [support page](https://github.com/sonaro-ai/Vaso3D-web-app).

---

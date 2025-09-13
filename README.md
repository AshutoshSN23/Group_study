# 📚 GroupStudy Platform - Real-Time Study Collaboration  

## 🚀 Project Overview  
GroupStudy Platform is a **real-time video conferencing application** designed for **seamless collaborative learning**. Unlike traditional platforms, it allows users to **instantly join study groups by simply typing a subject name**, eliminating the need for invite links. Users can **create rooms, join ongoing study sessions, and interact through video calls and chat messaging**, making group study more accessible and engaging.  

## ❗ Problem Statement  
In today’s digital learning environment, students face **limited interactive learning opportunities** and often feel **isolated in virtual classrooms**. Existing platforms lack **seamless study-based group collaboration**, relying on **manual invite links** and **complex setups** that hinder accessibility. **GroupStudy Platform** solves this by offering an intuitive, **subject-based joining system**, where students can **search, join, or create study rooms effortlessly**, fostering a more **engaging and interactive learning experience**.  

## ✨ Key Features  
🔑 **User Authentication** – Secure signup and login  
🎓 **Instant Room Joining** – Type a subject name to join without invite links  
🎥 **Real-time Video Conferencing** – Connect with multiple students via WebRTC  
💬 **Chat Messaging** – Text-based communication alongside video calls  
🏷 **User Presence Indicators** – See who joins or leaves the study group  
📜 **Persistent Chat History** – Messages remain for session duration  
🤖 **AI-Powered Doubt Resolution (Gemini AI)** – Get instant answers to academic doubts in real-time

## 🛠 Dependencies  
### Server-Side Dependencies 


```
json
{
  "cors": "^2.8.5",
  "cross-env": "^7.0.3",
  "dotenv": "^8.2.0",
  "express": "^4.17.1",
  "mongoose": "^8.9.2",
  "socket.io": "^2.3.0"
}
```


### Client-Side Dependencies
```
json
{
  "@google/generative-ai": "^0.21.0",
  "@testing-library/jest-dom": "^4.2.4",
  "@testing-library/react": "^9.3.2",
  "@testing-library/user-event": "^7.1.2",
  "axios": "^1.7.9",
  "cross-env": "^7.0.3",
  "react": "^16.13.1",
  "react-dom": "^16.13.1",
  "react-router-dom": "^5.3.4",
  "react-scripts": "3.4.1",
  "simple-peer": "9.6.2",
  "socket.io-client": "^2.3.0",
  "styled-components": "^5.1.0",
  "uuid": "^7.0.3"
}
```

## Setup Instructions  


### Installation  

1. **Clone the repository**  
   git clone <repository-url>  
   cd group-study-platform  

2. **Install server dependencies**  
   npm install  

3. **Install client dependencies**  
   cd client  
   npm install  
   cd ..  

4. **Environment Configuration**  

   Create a .env file in the root directory with the following variables:  

   MONGO_URI=mongodb://127.0.0.1:27017/groupstudydb  
   ### For production, use your MongoDB Atlas connection string  
   ### MONGO_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/groupstudydb  

5. **Start the server**  
   npm start  

6. **Start the client (in a separate terminal)**  
   cd client  
   npm start  

7. **Access the application**  

   Open your browser and navigate to:  

   https://your_ip:3000  

   or  

   https://localhost:3000  

## Deployment Guide

This guide will help you deploy the Group Study Platform to free hosting services.

### Prerequisites

1. Create accounts on the following services:
   - [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) (for database)
   - [Render](https://render.com/) (for hosting)

### Step 1: Set Up MongoDB Atlas

1. Sign up for a free MongoDB Atlas account
2. Create a new cluster (the free tier is sufficient)
3. Set up a database user with password
4. Add your IP to the IP Access List (or allow access from anywhere for development)
5. Get your MongoDB connection string from Atlas dashboard

### Step 2: Deploy to Render

Render offers a generous free tier and is easy to set up:

1. Sign up for a free Render account
2. From your dashboard, click "New" and select "Web Service"
3. Connect your GitHub repository (fork this repo to your GitHub account first)
4. Configure the service:
   - **Name**: group-study-platform (or any name you prefer)
   - **Environment**: Node
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`
   - **Plan**: Free

5. Add the following environment variables:
   - `NODE_ENV`: production
   - `MONGO_URI`: Your MongoDB Atlas connection string
   - `PORT`: 8080 (Render will override this)
   - `REACT_APP_GEMINI_API_KEY`: Your Gemini API key (if using this feature)

6. Click "Create Web Service"

Render will automatically build and deploy your application. Once deployed, you can access it via the provided URL.

### Alternative Free Hosting Options

#### Railway

1. Create a Railway account
2. Create a new project and connect your GitHub repository
3. Add a MongoDB service or connect to your MongoDB Atlas
4. Configure environment variables similar to Render
5. Deploy your application

#### Fly.io

1. Sign up for Fly.io
2. Install the Fly CLI
3. Run `fly launch` in your project directory
4. Configure environment variables
5. Deploy with `fly deploy`

### Updating Your Deployment

After making changes to your code:

1. Push changes to your GitHub repository
2. Render will automatically redeploy your application

### Troubleshooting

- If your application fails to build, check the build logs in Render
- Make sure all environment variables are correctly set
- Verify your MongoDB connection string is correct

## Usage Guide  

1. **Sign Up**  
   - Navigate to the signup page  
   - Enter your name and email  
   - Click "Sign Up"  

2. **Login**  
   - Navigate to the login page  
   - Enter your registered email  
   - Click "Login"  

3. **Create a Study Room**  
   - After logging in, you'll be directed to the create room page  
   - Enter the subject name and click "Create Room"  

4. **Join a Study Room**  
   - Search for an existing study room by subject name  
   - Share the room URL with others to invite them  

5. **Using the Study Group Platform**  
   - Grant camera and microphone permissions when prompted  
   - Use the chat feature to interact with other participants  
   - Collaborate using real-time video and text chat  

## Architecture  

The application follows a client-server architecture:  

- **Frontend**: React.js application with Socket.io client for real-time communication  
- **Backend**: Node.js with Express server, Socket.io for WebSocket connections  
- **Database**: MongoDB for user and study room storage  
- **Real-time Communication**: WebRTC (via simple-peer) for peer-to-peer video streaming  

## Future Plans  

- Enable real-time collaborative coding with syntax guidance  
- Implement screen sharing functionality  
- Add recording capabilities for study sessions  
- Develop mobile applications for iOS and Android  
- Implement user profiles with customizable settings  
- Add virtual background options  

## License  

This project is licensed under the MIT License - see the LICENSE file for details.  

## Contributors  

- Sachin Kiragi - Lead Developer  
- Ashutosh Naryagol - Developer  
 

## Troubleshooting  

If you encounter SSL certificate issues during development:  
1. For development purposes, the application can run on HTTP instead of HTTPS  
2. If using HTTPS, you may need to accept self-signed certificates in your browser  
3. For API requests, the application includes options to bypass SSL certificate validation in development mode

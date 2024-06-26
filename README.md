# Wanderlust - Your Ultimate Travel Blog 

WanderLust is a simple MERN travel blog website ✈ This project is aimed to help people to contribute in open source, upskill in react and also master git.

![Preview Image](https://github.com/krishnaacharyaa/wanderlust/assets/116620586/17ba9da6-225f-481d-87c0-5d5a010a9538)

## [Figma Design File](https://www.figma.com/file/zqNcWGGKBo5Q2TwwVgR6G5/WanderLust--A-Travel-Blog-App?type=design&node-id=0%3A1&mode=design&t=c4oCG8N1Fjf7pxTt-1)
## [Discord Channel](https://discord.gg/FEKasAdCrG)

## **Tutorial for Dockerization**

https://github.com/mayaworld13/wanderlust_three_tier_deploment/assets/127987256/00d2f805-c760-484a-807b-d6f0966d06ee




## 🎯 Goal of this project

At its core, this project embodies two important aims:



## Setting up the project locally

### Setting up the Backend

1. **Fork and Clone the Repository**

   ```bash
   git clone https://github.com/{your-username}/wanderlust.git
   ```

2. **Navigate to the Backend Directory**

   ```bash
   cd backend
   ```

3. **Install Required Dependencies**

   ```bash
   npm i
   ```

4. **Set up your MongoDB Database**

   - Open MongoDB Compass and connect MongoDB locally at `mongodb://localhost:27017`.

5. **Import sample data**

   > To populate the database with sample posts, you can copy the content from the `backend/data/sample_posts.json` file and insert it as a document in the `wanderlust/posts` collection in your local MongoDB database using either MongoDB Compass or `mongoimport`.

   ```bash
   mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray
   ```

6. **Configure Environment Variables**

   ```bash
   cp .env.sample .env
   ```

7. **Start the Backend Server**

   ```bash
   npm start
   ```

   > You should see the following on your terminal output on successful setup.
   >
   > ```bash
   > [BACKEND] Server is running on port 5000
   > [BACKEND] Database connected: mongodb://127.0.0.1/wanderlust
   > ```

### Setting up the Frontend

1. **Open a New Terminal**

   ```bash
   cd frontend
   ```

2. **Install Dependencies**

   ```bash
   npm i
   ```

3. **Configure Environment Variables**

   ```bash
   cp .env.sample .env.local
   ```

4. **Launch the Development Server**

   ```bash
   npm run dev --  --host
   ```

# WondarLust website  with React, Nodejs ,Mongodb and  Docker Setup

## Prerequisites

Before you begin, make sure you have the following installed:

- Docker
- Git (optional, for cloning the repository)

## Setup

1. Clone this repository (if you haven't already):

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```

2. Navigate to the project directory:

   ```bash
   cd your-repo-name
   ```

For frontend
   ```bash
   cd your-repo-name/frontend
   ```
1. Open the `.env.sample` file
   ```bash
   VITE_API_PATH="http://YOURIP:5000"
   ```
2. create a docker image from Dockerfile for frontend
   ```bash
   docker build -t frontend .
   ```

   - Now, make sure that you have created a network using following command
   ```bash
   docker network create threetier
   ```

For Backend
   ```bash
     cd your-repo-name/backend
   ```
1.  Open the `.env.sample` file
   ```bash
   MONGODB_URI="mongodb://YOURIP/wanderlust"
   ```
2. create a docker image from Dockerfile for frontend
   ```bash
   docker build -t backend .
   ```

 
- Attach all the three containers in the same network, so that they can communicate with each other
  
i) Mongodb container 
```bash
 docker run -d \
    --name mongodb \
    --network=threetier \
    -p 27017:27017 \
    mongo:latest
```
ii) Backend container
 ```bash
   docker run -d \
    --name backend \
    --network=threetier \
    -p 5000:5000 \
    backend:latest

 ```

iii) Frontend container
 ```bash
   docker run -d \
    --name frontend \
    --network=threetier \
    -p 5173:5173 \
    backend:latest

 ```

then open the `.env.sample` file of backend
   ```bash
   MONGODB_URI="mongodb://mongodb-containername/wanderlust"
   ```
then import sample data to featured section
 ```bash
    docker exec containername or id -it  mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray
   ```




If you find this project interesting and inspiring, please consider showing your support by starring it on GitHub! Your star goes a long way in helping me reach more developers and encourages me to keep enhancing the project.

🚀 Feel free to get in touch with me for any further queries or support, happy to help :)

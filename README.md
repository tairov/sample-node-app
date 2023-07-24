
# Sample Node.js App for Docker Deployment Testing

This repository contains a simple Node.js application named `app.js` and a Dockerfile to facilitate easy Docker deployments on different environments.

## Purpose

The main goal of this application is to serve as a testing ground for Docker deployments on various environments. It provides a basic Node.js web server using the Express framework to showcase how a Node.js application can be containerized with Docker.

## Prerequisites

Before running the Dockerized application, you need to have Docker installed on your system.

## Running the App with Docker

Follow these steps to run the sample Node.js app using Docker:

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/your-username/sample-node-app.git
   cd sample-node-app
   ```

2. Build the Docker image using the provided Dockerfile:

   ```bash
   docker build -t sample-node-app .
   ```

3. Run the Docker container from the built image:

   ```bash
   docker run -d -p 8080:8080 --name sample-node-app-container sample-node-app
   ```

   The application will start within the Docker container, and it will be accessible at [http://localhost:8080/](http://localhost:8080/).

## Routes

The application defines the following routes:

`curl` examples to run the endpoints of the sample Node.js app locally:

1. **GET /:**

   This endpoint returns a simple message indicating that the Node Sample App is up and running.

   ```bash
   curl http://localhost:8080/
   ```

   Output:

   ```
   Hello World!!! Node Sample App is up and running!
   ```

2. **GET /ping:**

   This endpoint returns "Pong!" as the response.

   ```bash
   curl http://localhost:8080/ping
   ```

   Output:

   ```
   Pong!
   ```

3. **POST /ping:**

   This endpoint returns "POST: Pong!" as the response.

   ```bash
   curl -X POST http://localhost:8080/ping
   ```

   Output:

   ```
   POST: Pong!
   ```

## Dockerfile

The repository includes a `Dockerfile` that sets up the Node.js environment, installs the app dependencies, and exposes port 8080 for communication with the outside world. The final image is based on the official Node.js Alpine image to keep it lightweight.

```Dockerfile
FROM node:alpine

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package.json .
RUN npm install

# Bundle app source
COPY . .

EXPOSE 8080

CMD [ "npm", "start" ]
```

## License

This project is licensed under the [MIT License](LICENSE).

Feel free to use this sample Node.js application and the provided Dockerfile as a starting point for your Docker deployments on different environments. Happy testing and coding!

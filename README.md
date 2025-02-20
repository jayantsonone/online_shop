Dockerizing the Code
I forked the original repository and cloned it to my local machine. After that, I created a Dockerfile to containerize the application.

Here's a breakdown of the Dockerfile:

FROM node:22.14.0-alpine: This starts with an official Node.js image based on the Alpine Linux distribution for a smaller footprint.

WORKDIR /app: Sets the working directory inside the container to /app, where the code will be placed.

COPY src/ .: Copies the source code from the src directory in the repository to the container's /app directory.

COPY . .: Copies the rest of the files from the repository to the container.

RUN npm install: Installs the required Node.js dependencies specified in package.json.

RUN npm run build: Runs the build script to prepare the app for production or development.

EXPOSE 5173: Exposes port 5173, which is typically used for development servers (e.g., for Vite.js apps).

CMD ["npm","run","dev"]: Specifies the command to start the development server using npm run dev.

This setup allows the app to be run inside a Docker container, making it easier to manage dependencies and environment configurations.

# Use official Node.js image as a base
FROM node:18-alpine AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (if it exists)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Expose the port your app will run on (adjust to your preferred port)
EXPOSE 5000

# Run the server with nodemon in development
CMD ["npm", "start"]

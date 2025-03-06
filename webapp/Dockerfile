# Use official Node.js image as a base
FROM node:18-alpine AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json (if it exists)
COPY package*.json ./

# Install dependencies
RUN npm install --legacy-peer-deps

# Copy the rest of the application files
COPY . .

# Build the application
RUN npm run build

# Use a smaller image for serving the app
FROM nginx:alpine

# Copy the build output to the nginx public directory
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80 to the outside
EXPOSE 80

# Start the nginx server to serve the build
CMD ["nginx", "-g", "daemon off;"]

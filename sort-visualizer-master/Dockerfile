# Stage 1: Build the React application
FROM node:14 AS build

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build --verbose

# Stage 2: Serve the app with Nginx
FROM nginx:alpine

# Copy the built files from the previous stage
COPY --from=build /usr/src/app/build /usr/share/nginx/html

# Expose the port the app runs on
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]

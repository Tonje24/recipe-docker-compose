# Use the lightweight Node.js 18 Alpine image
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package files first so dependencies are cached
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the backend code
COPY . .

# Create the folder where the SQLite database is stored
RUN mkdir -p /app/data

# The API runs on port 5000
EXPOSE 5000

# Start the server
CMD ["npm", "start"]

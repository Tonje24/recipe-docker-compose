# ---- Stage 1: Build the React app ----
FROM node:18-alpine AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package files first so dependencies are cached
COPY package*.json ./

# Install dependencies
RUN npm install

# Accept build argument
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

# Copy the rest of the frontend code
COPY . .

# Build the production version of the app
RUN npm run build

# ---- Stage 2: Serve the app with nginx ----
FROM nginx:alpine

# Copy the built files from the build stage into nginx
COPY --from=build /app/dist /usr/share/nginx/html

# nginx serves the app on port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]

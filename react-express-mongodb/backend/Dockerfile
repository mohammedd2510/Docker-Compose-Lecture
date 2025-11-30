# Use official Node.js image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install dependencies
RUN npm install 

# Copy source code
COPY . .

# Expose port (adjust based on your app)
EXPOSE 3000

# Start the app
ENTRYPOINT ["npm", "start"]

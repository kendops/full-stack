# Use Red Hat UBI 8 as the base image
FROM registry.redhat.io/ubi8/nodejs-22:latest

# Set working directory
WORKDIR /app

# Copy package files
COPY package.json yarn.lock ./

# Install required dependencies
RUN yarn install

# Copy the full project
COPY . .

# Install tools (React, Next.js, Gatsby, Material UI, etc.)
RUN yarn add react@19 jwt-decode@1.0.2 react-router-dom@7.1.3 \
    react-hot-toast@2.5.1 @mui/material@6.4.2 moment@2.30.1 \
    axios@1.7.9 react-icons@1 react-hook-form@7.54.2 \
    next@15.1.6 vite@5 gatsby@15.1.6

# Build frontend for production
RUN yarn build

# Expose frontend port (e.g., Next.js default port)
EXPOSE 3000

# Start frontend
CMD ["yarn", "start"]

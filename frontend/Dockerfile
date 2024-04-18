
#############Stage-1################
FROM node:21 AS builder

#Set a Work dir
WORKDIR /app

# Copy the package.json and package-lock.json for dependency installation
COPY package*.json ./

# Install Dependence
RUN npm i

#copy rest all code inside the container
COPY . .

#############Stage-2################
FROM node:21-slim

#Set a Work dir
WORKDIR /app

#copy built assets and dependecies from builder stage
COPY --from=builder /app .

# Copy the .env.sample file to .env.local
COPY .env.sample .env.local

# Expose port 5173 for thr node.js application
EXPOSE 5173

# Define the default command to run the application in development
CMD ["npm", "run", "dev","--","--host"]


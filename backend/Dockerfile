#------------Stage-1---------------
FROM node:21 AS builder
# Set a Working dir
WORKDIR /app

# Copy all code inside the container
COPY . .

RUN npm i
#------------Stage-2---------------
FROM node:21-slim

# Set a Working dir
WORKDIR /app

# Copy the above stage as compressed
COPY --from=builder /app .

COPY .env.sample .env 

#Port
EXPOSE 5000

#APP
CMD ["npm", "start"]

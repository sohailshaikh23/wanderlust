# Stage 1: build stage as backend-builder
FROM node:21

# setting up the working directory as /app
WORKDIR /app

# copy the application source code 
COPY . .

# Installing all the dependencies
RUN npm i


# Stage 2: Final stage
FROM node:21-slim

#Setting up the current working directory
WORKDIR /app

#Copy only the require dependency file from the backend-builder stage to the current stage
COPY --from=backend-builder /app .

# copy the environament variable file
COPY .env.sample .env

# Exposing the port 5000 for the application
EXPOSE 5000

# provide the default command to run the application
CMD ["npm","start"]

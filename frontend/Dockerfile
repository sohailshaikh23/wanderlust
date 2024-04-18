# Stage 1: Build stage named as frontend-builder
FROM node:21

# information about maintainer
LABEL maintainer="sohailshaikh125@gmail.com"

# Setting up the current working directory as /app
WORKDIR /app

# copy the package.json & package-lock.json to install the dependencies
COPY package*.json ./

# installing the dependencies
RUN npm install

# Copy the rest of the application code
COPY . .



# Stage 2 : Final stage
FROM node:21-slim

# Setting up the current working directory as /app
WORKDIR /app

# copy only the require dependencies from the frontend-builder stage to the Current stage
COPY --from=frontend-builder /app .

#Copy the environment varaible file 
COPY .env.sample .env.local

# Exposing the port 5173 for the application
EXPOSE 5173

# Provide the default command to run the application
CMD ["npm","run","dev","--","--host"]

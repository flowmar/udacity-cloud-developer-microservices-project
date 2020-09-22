# Use Ionic base image
FROM beevelop/ionic:latest AS ionic

# Create app directory in Docker
WORKDIR /usr/src/app

# Copy package.json & package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy app from local environment to Docker image
COPY . .

# Build Frontend
RUN ionic build

# Run nginx
FROM nginx:alpine

# Copy App to Nginx
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html
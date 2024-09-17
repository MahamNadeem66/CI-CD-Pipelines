version: '3.8'
services:
  webapp:
    image: dockerhubusername/webapp:latest
    ports:
      - "3000:3000"
    networks:
      - app-network

  db:
    image: postgres:alpine
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: appdb
    networks:
      - app-network

networks:
  app-network:
    driver: bridge
    
## Dockerfile (Application Image)
# Base image
FROM node:14-alpine

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./
RUN npm install

# Bundle app source
COPY . .

# Expose port and start application
EXPOSE 3000
CMD ["npm", "start"]

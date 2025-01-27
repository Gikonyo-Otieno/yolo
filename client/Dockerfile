# Use an official Node runtime as a parent image
FROM node:14-slim AS build

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Create a smaller final image to reduce size (for production)
FROM node:14-slim AS production

WORKDIR /app

COPY --from=build /usr/src/app /app

RUN npm install --only=production
RUN npm install -g serve

# Expose port 80 for production
EXPOSE 80

# Use environment variable for development or production mode
ENV ENVIRONMENT=production

# Command to run the app (for production or development)
CMD ["sh", "-c", "if [ \"$ENVIRONMENT\" = \"production\" ]; then serve -s build -l 80; else npm start; fi"]

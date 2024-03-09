# Use a specific version of node:xx-alpine to avoid bugs
FROM node:16-alpine as builder

# Set the working directory in the container
WORKDIR /app

# Copy the package.json file to the container's work directory
COPY package.json .

# Install dependencies in the container
RUN npm install

# Copy the rest of your app's source code from your host to your container's work directory
COPY . .

RUN npm run build

FROM nginx

COPY --from=builder /app/build /usr/share/nginx/html
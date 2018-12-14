# Frontend Image - https://hub.docker.com/_/node/
# This image comes with npm already installed
FROM node:8

# Create a container folder to have our files
WORKDIR /data

# Copy dependencies files
COPY ./www/package*.json ./
COPY ./www/webpack.config.js ./

# Install them
RUN cd /data && npm install

# Add source code
COPY ./www/src/ ./src/
#RUN ls -l ./

# Start npm
CMD [ "npm", "start" ]
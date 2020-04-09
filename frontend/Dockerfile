# Use an official node runtime as a parent image
FROM node:10

WORKDIR /frontend/

# Install dependencies
COPY package.json yarn.lock /frontend/

RUN npm install
RUN npm update

# Add rest of the client code
COPY . /frontend/

EXPOSE 3000

CMD npm start

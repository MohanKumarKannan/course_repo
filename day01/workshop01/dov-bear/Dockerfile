FROM node:21

WORKDIR /app

# now are inside app directory
# copy files from local into app directory (ADD & copy perform same thing. )
COPY main.js .
COPY package-lock.json .
COPY package.json .

## for directory you need to specify names 
COPY public public 
COPY views views

# Install dependencies
RUN npm ci

# How to run the application
ENV APP_PORT=3000
ENV INSTANCE_NAME="my Name is "
ENV INSTANCE_HASH=" HASH"

# Tell the container what port the application need
EXPOSE ${APP_PORT}


ENTRYPOINT node main.js
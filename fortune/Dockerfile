ARG VER=18.2.0

FROM node:${VER}

LABEL org.opencontainers.image.source=https://github.com/dtgw91/cfdsa-assignment-1

## building the image
# create a working directory 
WORKDIR /app

# ensure that curl is installed
RUN apt update && apt install curl

# copy the files from local into the container
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views
ADD main.js .

# install the packages
RUN npm ci

## run the image

ENV APP_PORT=3000

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s http://localhost:${APP_PORT}/healthz || exit 1


# run the appplication
ENTRYPOINT [ "node", "main.js" ]
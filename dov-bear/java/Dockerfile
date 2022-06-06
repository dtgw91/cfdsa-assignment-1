ARG VER=3.8.5-ibmjava-8

FROM maven:${VER}

LABEL developer=dan

## building the image
# create a working directory 
WORKDIR /app

# ensure that curl is installed
RUN apt update && apt install curl

# copy the files from local into the container
ADD mvnw.cmd .
ADD mvnw .
ADD pom.xml .
ADD src src

# install the packages
RUN mvn package

## run the image

ENV APP_PORT=3000

EXPOSE ${APP_PORT}

# run the appplication
ENTRYPOINT [ "mvn", "spring-boot:run" ]
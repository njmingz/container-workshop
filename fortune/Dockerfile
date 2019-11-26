FROM node:alpine

#Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000

#Create and change CWD to directory
WORKDIR ${APP_ROOT}

#Copy files into image.
#Files will be copied into CWD
ADD main.js .
ADD package.json .
ADD public public
ADD views views

#running commands
RUN npm i

EXPOSE ${APP_PORT}

RUN apk add curl

#add healthcheck
HEALTHCHECK --interval=30s --timeout=30s --retries=3 \
  CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1


#CMD vs ENTRYPOINT 
#=> can be overwritten by options passed into the contianer
#=> cannot be overwritten
ENTRYPOINT [ "node", "main.js" ]

#CMD is used as an empty field to append options
CMD [""]
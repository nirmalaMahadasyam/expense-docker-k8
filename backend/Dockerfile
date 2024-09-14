# alpine(tiny linux server underlane os we don't need may be dabian,rhel,centos etc...) on top of node:20 image
FROM node:20.15.0-alpine3.20
# just for info purpose
EXPOSE 8080
# connections b/w backend and db set up the env
ENV DB_HOST=mysql
# add group,adduser and mkdir and chage the access to the user to that directory
RUN addgroup -S expense && adduser -S expense -G expense \
    && mkdir /opt/server \
    && chown expense:expense -R /opt/server
 # pwd to move
WORKDIR /opt/server
# copy the .json,.js
COPY package.json .
COPY *.js /opt/server/
# to run npm install
RUN npm install
# secured to the nono root user
USER expense
EXPOSE 8081
# continously run our application
CMD [ "node","index.js" ]


######################
# multi-stage builds #
######################
# 1st build - image from it will be deleted after build thus saving the memory by excluding the cache of npm 
FROM node:20 as build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

# 2nd build
FROM node:20.18.0-alpine3.20
EXPOSE 8080
ENV DB_HOST="mysql"
RUN addgroup -S expense && adduser -S expense -G expense && \
    mkdir /opt/server && \
    chown -R expense:expense /opt/server
WORKDIR /opt/server
# copy the output of 1st build to 2nd build
COPY --from=build /opt/server /opt/server
USER expense
CMD ["node", "index.js"]

#####################################
# after implementing best practices #
#####################################
# # using minimal image
# FROM node:20.18.0-alpine3.20
# EXPOSE 8080
# ENV DB_HOST="mysql"
# # combining the commands to reduce no.of layers and so the build time
# RUN addgroup -S expense && adduser -S expense -G expense && \
#     mkdir /opt/server && \
#     chown -R expense:expense /opt/server
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# # Run the container as non-root user -- improving the security
# USER expense
# CMD ["node", "index.js"]


########################
# before best practice #
########################
# FROM node:20
# EXPOSE 8080
# ENV DB_HOST="mysql"
# RUN mkdir /opt/server
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install
# CMD ["node", "index.js"]
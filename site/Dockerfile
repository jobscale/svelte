# IMPORTANT: Don't use this Dockerfile in your own projects without also looking at the .dockerignore file.
# Without an appropriate .dockerignore, this Dockerfile will copy a large number of unneeded files into your image.

FROM mhart/alpine-node:14

# install dependencies
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --production

###
# Only copy over the Node pieces we need
# ~> Saves 35MB
###
FROM mhart/alpine-node:slim-14

WORKDIR /app
COPY --from=0 /app .
COPY . .

EXPOSE 3000
CMD ["node", "build"]

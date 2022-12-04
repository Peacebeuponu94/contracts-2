FROM node:14-alpine3.13@sha256:669b22aaccf744c992ec2390db88ff3fa449f1b1421565423f2866f3807e14b7

# Create app directory
WORKDIR /usr/src/app/

COPY . .

RUN apk add --no-cache tini git python3 linux-headers eudev-dev libusb-dev build-base
# Tini is now available at /sbin/tini

RUN yarn install --frozen
RUN yarn build

# Run Node app as child of tini
# Signal handling for PID1 https://github.com/krallin/tini
ENTRYPOINT ["/sbin/tini", "--"]

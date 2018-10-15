ARG NODE_VERSION=6
FROM node:${NODE_VERSION}

# Home directory for Node-RED application source code.
RUN mkdir -p /node-red

# User data directory, contains flows, config and nodes.
RUN mkdir /data

WORKDIR /node-red

# Add node-red user so we aren't running as root.
#RUN useradd --home-dir /usr/src/node-red --no-create-home node-red \
#    && chown -R node-red:node-red /data \
#    && chown -R node-red:node-red /usr/src/node-red

# USER node-red

# package.json contains Node-RED NPM module and node dependencies
COPY package.json /node-red/
RUN npm install

# User configuration directory volume
EXPOSE 1880

# Environment variable holding file path for flows configuration
ENV FLOWS=flows.json
ENV NODE_PATH=/node-red/node_modules:/data/node_modules

CMD ["npm", "start", "--", "--userDir", "/data"]

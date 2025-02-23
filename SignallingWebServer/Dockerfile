# Use the current Long Term Support (LTS) version of Node.js
FROM node:lts

# Copy the signalling server and frontend source code from the build context
COPY /SignallingWebServer /app/SignallingWebServer
COPY /Frontend /app/Frontend

WORKDIR /app

# Install the dependencies for the signalling server and build the frontend
RUN SignallingWebServer/platform_scripts/bash/setup.sh --build

# Expose TCP ports 80 and 443 for player WebSocket connections and web server HTTP(S) access
EXPOSE 80
EXPOSE 443

# Expose TCP port 8888 for streamer WebSocket connections
EXPOSE 8888

# Expose TCP port 8889 for connections from the SFU
EXPOSE 8889

# Expose TCP port 9999 for connections from the Matchmaker
EXPOSE 9999

# Set the signalling server as the container's entrypoint
ENTRYPOINT ["node", "/SignallingWebServer/cirrus.js"]

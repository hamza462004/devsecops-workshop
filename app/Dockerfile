FROM node:18-alpine
WORKDIR /app

# We are building from the root, so we look into the app/ folder
COPY app/package*.json ./
RUN npm install
COPY app/ .

EXPOSE 3000
CMD ["node", "index.js"]

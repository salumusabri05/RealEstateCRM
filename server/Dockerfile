FROM node:18-slim

WORKDIR /app

# Install system dependencies for build tools and Puppeteer / Chromium
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    make \
    g++ \
    chromium \
    fonts-liberation \
    && rm -rf /var/lib/apt/lists/*

ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true \
    PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium

COPY package*.json ./

RUN npm install --legacy-peer-deps

COPY . .

EXPOSE 5001

CMD ["node", "index.js"]

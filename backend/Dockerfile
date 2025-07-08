# 1) Base image
FROM node:20-alpine

# 2) Create app directory
WORKDIR /app

# 3) Install dependencies
COPY package*.json ./
COPY nx.json ./
COPY tsconfig.base.json ./
COPY libs ./libs
COPY apps/backend ./apps/backend

RUN npm install

# 4) Build backend
RUN npm run build backend

# 5) Start backend
CMD ["node", "dist/apps/backend/main.js"]

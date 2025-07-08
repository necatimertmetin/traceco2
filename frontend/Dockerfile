# 1) Base image
FROM node:20-alpine

# 2) Create app directory
WORKDIR /app

# 3) Install dependencies
COPY package*.json ./
COPY nx.json ./
COPY tsconfig.base.json ./
COPY libs ./libs
COPY apps/frontend ./apps/frontend

RUN npm install

# 4) Build frontend
RUN npm run build frontend

# 5) Use nginx or serve static
# Simple way: Use 'serve' package
RUN npm install -g serve

# 6) Start frontend
CMD ["serve", "-s", "dist/apps/frontend", "-l", "3000"]

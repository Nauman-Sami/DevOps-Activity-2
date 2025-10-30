FROM node:20-alpine

WORKDIR /app

# --------------------
# Backend setup
# --------------------
WORKDIR /app/backend
COPY backend/package*.json ./
RUN npm install
COPY backend ./

# --------------------
# Frontend setup
# --------------------
WORKDIR /app/frontend
COPY frontend/package*.json ./
RUN npm install
COPY frontend ./

RUN npm install -g concurrently

EXPOSE 8080 5173

WORKDIR /app

CMD ["concurrently", "npm --prefix backend start", "npm --prefix frontend run dev"]

# Build stage

FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install 

COPY . .


# Run stage

FROM node:22-alpine

WORKDIR /app

COPY --from=builder /app/node_modules ./node_modules

COPY --from=builder /app/index.js ./index.js

COPY --from=builder /app/ .

EXPOSE 8000

CMD ["node","index.js"]

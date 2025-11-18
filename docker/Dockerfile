# --- Build stage ---
FROM node:20-alpine AS build
WORKDIR /app

COPY app/package*.json ./
RUN npm install --omit=dev

COPY app/ ./ 
# (Optional: run tests)
# RUN npm test

# --- Runtime stage ---
FROM node:20-alpine
WORKDIR /app

COPY --from=build /app /app

ENV NODE_ENV=production
EXPOSE 3000

CMD ["npm", "start"]

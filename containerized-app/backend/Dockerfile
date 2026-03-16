# ---------- Builder Stage ----------
FROM node:20-alpine AS builder

WORKDIR /app

# Copy only package files first (better caching)
COPY package*.json ./

RUN npm install --only=production

# Copy source code
COPY src ./src


# ---------- Production Stage ----------
FROM node:20-alpine

WORKDIR /app

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Copy from builder
COPY --from=builder /app /app

USER appuser

EXPOSE 3000

CMD ["node", "src/server.js"]
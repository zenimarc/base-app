# Development stage
FROM node:18 AS development

# Create and change to the app directory
WORKDIR /app

# Copy application dependency manifests to the container image
COPY package*.json pnpm-lock.yaml ./

# Install dependencies
RUN npm install -g pnpm
RUN pnpm i

# Copy the local code to the container image
COPY . .

# Run the app in development mode
CMD ["pnpm", "dev"]

# Build stage
FROM node:18 AS build

# Create and change to the app directory
WORKDIR /app

# Copy application dependency manifests to the container image
COPY package*.json pnpm-lock.yaml ./

# Install dependencies
RUN npm install -g pnpm && pnpm install

# Copy the local code to the container image
COPY . .

# Build the app
RUN pnpm build

# Production stage
FROM node:18 AS production

# Create and change to the app directory
WORKDIR /app

# Copy built files from the build stage
COPY --from=build /app ./

# Install production dependencies
RUN npm install -g pnpm && pnpm install --production

# Run the app in production mode
CMD ["node", "build"]

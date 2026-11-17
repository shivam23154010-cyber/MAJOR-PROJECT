FROM node:22-alpine

# Enable pnpm 9 matching the project's lockfileVersion '9.0'
RUN corepack enable && corepack prepare pnpm@9 --activate

WORKDIR /app

# Copy package descriptors
COPY package.json pnpm-lock.yaml ./

# Install dependencies
RUN pnpm install --frozen-lockfile

# Copy application source
COPY . .

EXPOSE 4200

# Start Angular development server accessible from outside container
CMD ["pnpm", "exec", "ng", "serve", "--host", "0.0.0.0"]

FROM node:24.11.1-alpine AS builder
WORKDIR /frontend
COPY angular-nestjs-realworld-example-app/ /frontend/
RUN corepack enable
RUN pnpm install --frozen-lockfile
RUN pnpm --filter @monorepo/client build
FROM node:24.11.1-alpine AS runner
WORKDIR /frontend
COPY --from=builder /frontend/apps/client/dist/client ./
CMD ["node", "server/server.mjs"]

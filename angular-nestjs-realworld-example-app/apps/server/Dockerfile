    FROM node:24.11.1-alpine
    WORKDIR /backend
    COPY angular-nestjs-realworld-example-app/ /backend/
    RUN corepack enable
    RUN pnpm install --frozen-lockfile
    RUN cd /backend && pnpm turbo run build --filter=@monorepo/server
    EXPOSE 4000
    CMD ["sh", "-c", "cd /backend/packages/database && pnpm prisma migrate deploy && cd /backend/apps/server && node dist/main.js"]

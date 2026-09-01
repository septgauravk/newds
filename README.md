# Deployment notes for Vercel

This app is structured as a single Express server that serves the built frontend and the API routes.

## Required Vercel setup

1. Add the project to Vercel.
2. Set the Root Directory to the repository root.
3. Add these environment variables in the Vercel dashboard:
   - `NODE_ENV=production`
   - `JWT_SECRET`
   - `DATABASE_URL`
   - `OAUTH_SERVER_URL`
   - `OWNER_OPEN_ID`
   - `VITE_APP_ID`
   - `BUILT_IN_FORGE_API_URL` (optional)
   - `BUILT_IN_FORGE_API_KEY` (optional)
4. Deploy.

## Local checks

```bash
pnpm install
pnpm check
pnpm build
pnpm start
```

## Notes

- The app uses Express and serves the built frontend from `dist/public`.
- Vercel needs the server entrypoint to be a web-compatible handler; this project includes a `vercel.json` configuration to route all requests to the server.
- If your database is MySQL, set `DATABASE_URL` to a connection string that Vercel can reach, or use a managed database service with a public/private network path.

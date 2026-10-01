# Corespawn.pl

Responsive Corespawn landing page built with Vue 3, Inertia.js, and Vite. The site is English-first, with Polish available from the language switcher.

## Run locally

Node.js 20 or newer is required.

```bash
npm ci
npm run dev
```

Open the address shown by Vite (usually `http://localhost:5173`).

## Production build

```bash
npm run build
```

The generated static files are in `dist/`.

## Publish to GitHub

Repository: [github.com/Ikabytez/corespawn](https://github.com/Ikabytez/corespawn).

To publish future changes, run this from the project directory:

```bash
git add -A
git commit -m "Describe the changes"
git push
```

For cloning and deploying to a VPS, see the [deployment guide](./deploy/README.md).

The Ubuntu/Debian deployment guide for Nginx and Let's Encrypt is in [deploy/README.md](./deploy/README.md), and the Nginx config is in [deploy/nginx/corespawn.pl.conf](./deploy/nginx/corespawn.pl.conf).

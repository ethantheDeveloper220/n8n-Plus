# Self-Hosting n8n

n8n is an open-source workflow automation tool. This guide will help you self-host n8n on your own server or local machine.

---

## 1. Prerequisites
- **Docker** (recommended) or **Node.js** (v18+)
- Git (optional, for development)
- At least 2GB RAM

---

## 2. Quick Start with Docker (Recommended)

### Install Docker
- [Download Docker Desktop](https://www.docker.com/products/docker-desktop/) and install it for your OS.

### Start n8n with Docker
```sh
docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
```
- Access n8n at: [http://localhost:5678](http://localhost:5678)
- Data is stored in your home directory under `.n8n`.

#### On Windows, use:
```sh
docker run -d --name n8n -p 5678:5678 -v C:/Users/<YourUser>/.n8n:/home/node/.n8n n8nio/n8n
```

### Stopping/Restarting n8n
```sh
docker stop n8n
# To restart:
docker start n8n
```

---

## 3. Advanced: Use Your Own Database
Set environment variables for Postgres, MySQL, etc. Example for Postgres:
```sh
docker run -d --name n8n -p 5678:5678 \
  -e DB_TYPE=postgresdb \
  -e DB_POSTGRESDB_HOST=host.docker.internal \
  -e DB_POSTGRESDB_DATABASE=n8n \
  -e DB_POSTGRESDB_USER=n8n \
  -e DB_POSTGRESDB_PASSWORD=password \
  n8nio/n8n
```

---

## 4. Running n8n with Node.js (Development or Customization)

### Install Node.js (v18+)
- [Download Node.js](https://nodejs.org/)

### Clone the Repo and Install Dependencies
```sh
git clone https://github.com/n8n-io/n8n.git
cd n8n
pnpm install # or yarn install / npm install
```

### Build and Start n8n
```sh
pnpm build
pnpm start
```
- Access at: [http://localhost:5678](http://localhost:5678)

### For Development (with Hot Reload)
```sh
pnpm dev
```

---

## 5. Using Your Local Frontend Code with Docker

By default, Docker uses the built-in frontend. To use your local changes:
1. Build the frontend:
   ```sh
   cd packages/frontend
   pnpm build
   ```
2. Build a custom Docker image or mount the `dist` folder into the container (advanced).

---

## 6. Environment Variables & Configuration
- See the [n8n docs](https://docs.n8n.io/) for all available environment variables (auth, database, etc).
- You can set variables with `-e` in Docker or in a `.env` file for Node.js.

---

## 7. Updating n8n
- With Docker: `docker pull n8nio/n8n` then restart the container.
- With Node.js: `git pull` and rebuild (`pnpm build`).

---

## 8. Troubleshooting
- Check logs: `docker logs n8n` or see terminal output for Node.js.
- Make sure ports are not blocked (default: 5678).
- For more help, visit the [n8n Community Forum](https://community.n8n.io/).

---

## 9. Security Tips
- Set up authentication: [n8n docs - Security](https://docs.n8n.io/hosting/security/)
- Use HTTPS in production.
- Regularly update your instance.

---

## 10. Useful Links
- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community](https://community.n8n.io/)
- [n8n GitHub](https://github.com/n8n-io/n8n)

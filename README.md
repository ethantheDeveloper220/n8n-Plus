# n8n PLUS: Self-Host & Enhanced Features Guide

## 🚀 Quick Start: Cloning & Running This Project

1. **Clone the repository:**
   ```sh
   git clone https://github.com/ethantheDeveloper220/n8n-Plus.git
   cd n8n-Plus
   ```

2. **(Recommended) Start with Docker:**
   - Make sure you have [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed.
   - Run:
     ```sh
     docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
     ```
   - On Windows, use:
     ```sh
     docker run -d --name n8n -p 5678:5678 -v C:/Users/<YourUser>/.n8n:/home/node/.n8n n8nio/n8n
     ```
   - Open [http://localhost:5678](http://localhost:5678) in your browser.

3. **(Alternative) Run with Node.js for Development:**
   - Install [Node.js v18+](https://nodejs.org/)
   - Install dependencies:
     ```sh
     pnpm install # or yarn install / npm install
     ```
   - Build and start:
     ```sh
     pnpm build
     pnpm start
     ```
   - For hot-reload development:
     ```sh
     pnpm dev
     ```

4. **Push your changes (if you have write access):**
   ```sh
   git add .
   git commit -m "Describe your changes"
   git push
   ```

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
git clone https://github.com/ethantheDeveloper220/n8n-Plus.git
cd n8n-Plus
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

# 🚀 Enhanced Features in This Build(coming Soon🤫)

## 🎨 Multiple Web Themes
- Choose from 6+ themes (Dark, Light, Blue, Green, High-Contrast, Purple, etc.)
- Go to **Settings > Personalisation > Theme** to select your preferred look.

## ⚙️ Usable Settings
- Language selection
- Date/time format
- Notification preferences
- Editor preferences (font size, monospace, auto-save)
- Accessibility options (font scaling, reduced motion)
- Default start page
- Privacy settings (analytics/telemetry opt-in/out)
- Keyboard shortcuts enable/disable

## 🤖 AI Workflow Maker
- Create workflows by describing them in plain English!
- Click the **AI Workflow Maker** button at the top of the workflow list.
- Enter your workflow idea (e.g., "When I get an email, save the attachment to Google Drive and notify me on Slack.")
- Preview and import the generated workflow (AI integration is pluggable for local models).

## 🛠️ More Workflow Features
- Workflow templates gallery
- Workflow versioning/history
- Workflow sharing/collaboration
- Workflow scheduling/cron UI
- Workflow analytics/insights

---

## Useful Links
- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community](https://community.n8n.io/)
- [n8n GitHub](https://github.com/n8n-io/n8n)

---

Enjoy your powerful, self-hosted n8n instance with all the latest features!



n8n Self hosting and Setup guide is below

































































![Banner image](https://user-images.githubusercontent.com/10284570/173569848-c624317f-42b1-45a6-ab09-f0ea3c247648.png)

# n8n - Secure Workflow Automation for Technical Teams

n8n is a workflow automation platform that gives technical teams the flexibility of code with the speed of no-code. With 400+ integrations, native AI capabilities, and a fair-code license, n8n lets you build powerful automations while maintaining full control over your data and deployments.

![n8n.io - Screenshot](https://raw.githubusercontent.com/n8n-io/n8n/master/assets/n8n-screenshot-readme.png)

## Key Capabilities

- **Code When You Need It**: Write JavaScript/Python, add npm packages, or use the visual interface
- **AI-Native Platform**: Build AI agent workflows based on LangChain with your own data and models
- **Full Control**: Self-host with our fair-code license or use our [cloud offering](https://app.n8n.cloud/login)
- **Enterprise-Ready**: Advanced permissions, SSO, and air-gapped deployments
- **Active Community**: 400+ integrations and 900+ ready-to-use [templates](https://n8n.io/workflows)

## Quick Start

Try n8n instantly with [npx](https://docs.n8n.io/hosting/installation/npm/) (requires [Node.js](https://nodejs.org/en/)):

```
npx n8n
```

Or deploy with [Docker](https://docs.n8n.io/hosting/installation/docker/):

```
docker volume create n8n_data
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

Access the editor at http://localhost:5678

## Resources

- 📚 [Documentation](https://docs.n8n.io)
- 🔧 [400+ Integrations](https://n8n.io/integrations)
- 💡 [Example Workflows](https://n8n.io/workflows)
- 🤖 [AI & LangChain Guide](https://docs.n8n.io/langchain/)
- 👥 [Community Forum](https://community.n8n.io)
- 📖 [Community Tutorials](https://community.n8n.io/c/tutorials/28)

## Support

Need help? Our community forum is the place to get support and connect with other users:
[community.n8n.io](https://community.n8n.io)

## License

n8n is [fair-code](https://faircode.io) distributed under the [Sustainable Use License](https://github.com/n8n-io/n8n/blob/master/LICENSE.md) and [n8n Enterprise License](https://github.com/n8n-io/n8n/blob/master/LICENSE_EE.md).

- **Source Available**: Always visible source code
- **Self-Hostable**: Deploy anywhere
- **Extensible**: Add your own nodes and functionality

[Enterprise licenses](mailto:license@n8n.io) available for additional features and support.

Additional information about the license model can be found in the [docs](https://docs.n8n.io/reference/license/).

## Contributing

Found a bug 🐛 or have a feature idea ✨? Check our [Contributing Guide](https://github.com/n8n-io/n8n/blob/master/CONTRIBUTING.md) to get started.

## Join the Team

Want to shape the future of automation? Check out our [job posts](https://n8n.io/careers) and join our team!

## What does n8n mean?

**Short answer:** It means "nodemation" and is pronounced as n-eight-n.

**Long answer:** "I get that question quite often (more often than I expected) so I decided it is probably best to answer it here. While looking for a good name for the project with a free domain I realized very quickly that all the good ones I could think of were already taken. So, in the end, I chose nodemation. 'node-' in the sense that it uses a Node-View and that it uses Node.js and '-mation' for 'automation' which is what the project is supposed to help with. However, I did not like how long the name was and I could not imagine writing something that long every time in the CLI. That is when I then ended up on 'n8n'." - **Jan Oberhauser, Founder and CEO, n8n.io**

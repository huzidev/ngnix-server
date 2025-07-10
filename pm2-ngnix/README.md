# 🚀 PM2 & PuTTY Guide for NGINX Server Management

## 🔐 Connecting to the Server via PuTTY

Follow the steps provided in this repository:  
➡️ [Connect via PuTTY](https://github.com/huzidev/ngnix-server/tree/master/puTTY)

Once connected to your server via SSH, you can begin managing your Node.js applications with PM2.

---

## 📊 PM2 Basic Commands

| Command               | Description                                   |
|-----------------------|-----------------------------------------------|
| `pm2 status`          | View status of all running services           |
| `pm2 log`             | View live logs for all services               |
| `pm2 logs [name]`     | View logs for a specific service              |
| `pm2 restart [name]`  | Restart a specific service                    |
| `pm2 stop [name]`     | Stop a specific service                       |
| `pm2 start [file]`    | Start a service using a file (e.g., app.js)   |
| `pm2 delete [name]`   | Remove a service from PM2                     |

Example:

```bash
pm2 status
pm2 logs main
pm2 restart main
```

---

## 📁 File & Directory Navigation

- `ls`: List all files and folders
- `cd [folder]`: Navigate into a directory

Example:

```bash
cd /home/apps
ls
```

> Services that are running will appear in **blue** in PM2 (indicating folders).

---

## 🔑 SSH Keys (.pub Files)

`.pub` files are **public SSH keys**. These must be added to the appropriate repository:

**GitHub → Repo → Settings → Deploy Keys → Add Key**

Example:

- If you see a key file like `id_rsa.pub`, copy its contents:
  
  ```bash
  cat ~/.ssh/id_rsa.pub
  ```

- Then paste it into GitHub's Deploy Keys section.

---

## ⚙️ ecosystem.config.js

This file contains PM2’s ecosystem configuration.

Key fields:

- `script`: Command to run the application (e.g., `server.js`)
- `cwd`: Current working directory (path to your app)

Example:

```js
module.exports = {
  apps: [
    {
      name: "main",
      script: "server.js",
      cwd: "/home/apps/main",
      watch: true
    }
  ]
};
```

View the file with:

```bash
cat /home/apps/main/ecosystem.config.js
```

---

## 🧩 Viewing File Contents

Use the `cat` command to view files directly in terminal.

Examples:

```bash
cat ~/.ssh/config
cat ecosystem.config.js
cat package.json
```

---

## 🔄 Git Commands for Updates

Before making changes, navigate to the correct project folder:

```bash
cd /home/apps/main  # or admin/api depending on service
```

Then run:

```bash
git pull
```

- If `package.json` has changed:

```bash
npm install
```

- If no package changes:

```bash
pm2 restart main
```

Use `pm2 logs` to check live logs:

```bash
pm2 logs main
```

---

## ✅ Example Flow: Deploy Update to `main` App

```bash
cd /home/apps/main
git pull
npm install         # Only if package.json was updated
pm2 restart main
pm2 logs main
```

---

## 📘 Extra Tips

- Use `pm2 save` to persist your PM2 process list after reboot.
- Use `pm2 startup` to configure PM2 to launch on boot.
- To monitor PM2 in real-time: `pm2 monit`

---
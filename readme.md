# Foundry VTT Server Quick Guide

This document explains how to access, manage, and restart your Foundry VTT server.

---

## 1. Access the Server
To connect to the server via SSH, run:

```bash
ssh -i ~/.ssh/foundryprivate.pem ubuntu@193.122.142.204
```
Attention to the ip on the command above, it needs to be current one
---

## 2. Manage the Foundry Process

- **Check the status of the server:**
  ```bash
  pm2 list
  ```

- **Start Foundry if it is stopped:**
  ```bash
  pm2 start node --name foundry -- /home/ubuntu/foundry/resources/app/main.js --dataPath=/home/ubuntu/foundryuserdata
  ```

- **Save the current process list (so Foundry starts automatically on reboot):**
  ```bash
  pm2 save
  ```

- **Enable Foundry to start with the system:**
  ```bash
  pm2 startup systemd
  ```

---

## 3. Restarting the Server

Normally you won’t need to restart the whole server.  
If necessary, you can reboot with:

```bash
sudo reboot
```

---

## 4. Dynamic DNS (No-IP)

Dynamic DNS keeps your hostname updated if the server’s IP changes.

- **Check if the No-IP service is running:**
  ```bash
  ps aux | grep noip2
  ```
  ✅ You should see a process like `/usr/local/bin/noip2`.

- **Check current No-IP status:**
  ```bash
  sudo /usr/local/bin/noip2 -S
  ```

This confirms that your DNS is updating correctly.

---

## Notes
- Normally you only need to check the server status with `pm2 list`.  
- Restart or reconfigure only if something isn’t working.  
- Keep your SSH key (`foundryprivate.pem`) safe — it is required for access.

---

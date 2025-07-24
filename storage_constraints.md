# 💾 Storage Constraints & Management in Rootless Mode
On school machines, projects must be containerized using Docker and run inside user writable areas like /goinfre or /sgoinfre.
These directories have limited space and no root permissions, so storage efficiency is critical. **check school computer for availbe space in /goinfre**

## ⚖️ Typical Disk Usage Breakdown (Estimates)

| Component                | Approx Size       | Notes                                                |
|--------------------------|-------------------|------------------------------------------------------|
| Node.js Backend Image    | 300–700MB         | Varies by base image and installed packages          |
| Frontend Build Output    | 100–300MB         | Depends on framework and production build            |
| PostgreSQL Image         | ~200MB + volume   | DB volume adds size over time                        |
| Docker Layers & Cache    | 500MB–2GB         | Build cache, image layers, unused containers         |
| Log Files & Temp Data    | ~50MB–500MB       | Generated during runtime unless cleaned manually     |
| Source Code Repos        | ~50MB–500MB       | Includes frontend, backend, config, assets           |
| Package Managers         | 100MB–1GB         | e.g. `node_modules`, `pip`, `cargo` during local build |

### 🧱 Why Storage Matters in ft_transcendence
- /goinfre is limited, it's shared across your user session and often capped
- Rootless Docker can't mount external disks or bind host folders easily
- Image rebuilds can generate multiple layers and duplicates
- Accumulated logs, build artifacts, and caches stay unless removed manually

### 🛠️ Good Practices for Storage Optimization
- 🧹 Prune regularly: ```bash docker system prune -a docker volume prune``` Removes unused containers, layers, and volumes safely
- 📦 Use slim base images: Alpine-based variants (e.g. node:alpine, postgres:alpine, nginx:alpine) drastically reduce image size
- ✂️ Multi-stage Docker builds: Strip dev dependencies before finalizing production image
- 🎯 Keep rebuilds minimal: Structure Dockerfile so only changed files (e.g. /src) trigger new layers
- 🔗 Named volumes over bind-mounts: Avoid mounting host folders — use internal Docker volumes for persistent but isolated data

### 💡 Optional Additions
- Consider tracking volume sizes via docker system df
- Add warnings if container setup detects low space in /goinfre
- Include cleanup steps in a Makefile such as
  ```docker system prune -af
    docker volume prune -f
  ```

<details>
<summary><strong>One-Liners to Clean Out User-Level Bloat</strong></summary>
  
You can run these to free up space, but always check first:

```bash
# Clear most language/tool caches
rm -rf ~/.cache/* ~/.config/* ~/.local/share/*

# Remove VSCode extensions and crash logs
rm -rf ~/.vscode ~/.config/Code ~/.config/VSCodium

# Clean up large package folders
rm -rf node_modules dist .parcel-cache .cache .next target

# Prune Docker (containers, volumes, images)
docker system prune -af
docker volume prune -f

# Check largest folders in your home directory
du -sh ~/* | sort -h
```

⚠️ Do NOT run these blindly if you have critical data tucked into those folders. But for testing, sandboxed builds, and workspace resets, they can be helpfull.

🧹 Clear Common Caches
Node modules, frontend builds, package locks:
```bash
rm -rf node_modules
rm -rf dist
rm -rf .cache
```

- Check available space in /goinfre
    - df -h /goinfre

- View the size of specific folders
    - du -sh /goinfre/*

**Add any cleanup tips here**
</details>
  

# Selfhost-Minecraft
This is a overview on how I selfhosted my own minecraft server on my ubuntu server and manage to make it accessible to friends. I used [`itzg/minecraft-server`](https://github.com/itzg/docker-minecraft-server) image and made a tunnel via [playit.gg](https://playit.gg) so that anyone could connect without the need for port fowarding.

### What you need before you start
- A [playit.gg](https://playit.gg) account and agent secret key (this will go into the .env file later for saftey)

### 1. Clone the repo
 
```bash
git clone https://github.com/your-username/your-repo.git
cd you
```
### 2. Run Ansible to get the dependancies you need
 
Run the playbook to install Docker on your server:
 
```bash
ansible-playbook -i inventory.ini playbook.yml
```

### 3. Create your `.env` file
 
```bash
.env
```
 
Then fill in your secrets:
 
```env
MC_RCON_PASSWORD=your_secure_rcon_password
PLAYIT_SECRET_TOKEN=your_playit_agent_token
```

### 4. Start the server
 
```bash
docker compose up -d
```

## Useful Commands
 
| Action | Command |
|---|---|
| Start server | `docker compose up -d` |
| Stop server | `docker compose stop` |
| Restart server | `docker compose restart` |
| Check status | `docker compose ps` |
| View MC logs | `docker compose logs -f mc` |
| View tunnel logs | `docker compose logs -f playit` |


## Ports that are being used
| Port | Purpose |
|---|---|
| `25565` | Minecraft |
| `25575` | RCON |

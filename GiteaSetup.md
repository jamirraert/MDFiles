1. create directory folder
```
mkdir gitea
```

2. go to gitea folder
```
cd gitea
```

3. create docker-compose.yml and add this block of code
```
version: "3"

services:
  server:
    image: gitea/gitea:latest
    container_name: gitea
    restart: always
    environment:
      - USER_UID=1000
      - USER_GID=1000
    volumes:
      - ./data:/data
      - ./custom:/app/gitea/custom
      - ./log:/app/gitea/log
    ports:
      - "3000:3000"
      - "2222:22"
```

4. Install Docker Compose:
```
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

Verify Docker Compose Installation:
```
docker-compose --version
```

5. create image by running this code
```
docker-compose up -d
```

6. Run this
```
docker-compose logs
```
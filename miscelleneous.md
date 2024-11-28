## 1. Docker compose frontend was not running on 3002 but on was all other ports:
 Issue: the frontend of openwebui was running at `localhost:3000` or any other port but not at `localhost:3002` as mentioned in the problem statement.
 Docker-compose snippet:
```
  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    volumes:
      - .data/open-webui:/app/backend/data
    depends_on:
      - ollama
    ports:
      - 3002:8080
    environment:
      - 'OLLAMA_BASE_URL=http://ollama:11434'
    extra_hosts:
      - host.docker.internal:host-gateway
    networks:
      - ollama
```
Issue was cache in browser, so I cleared the cache(just 'cached images and files') and it worked fine.

Might have been: an old docker image was running cached in the browser, so it was not showing the upadated frontend on that specific port.

## 2. 


---
title: "Running Ollama in remote Mac Mini"
format: html
date: 2024-08-20
---

I have a Mac Mini running in my LAN. It is configured as `mini` in `/etc/hosts` in my local host (which is a Macbook Air). 
We will try to do all the steps on command line, so that we need not access the Mac Mini desktop. 

### Remote Server: Install and start Ollama
Do these steps on the remote server
```shell
# Install Ollama on the remote server
brew install ollama --cask

# Set OLLAMA_HOST, so that the server can be accessible remotely 
export OLLAMA_HOST='0.0.0.0'

# Start Ollama
ollama serve
```
OLLAMA_HOST can be added to the .bashrc or .zshrc to avoid setting it each time. 

### On Localhost

##### 1. Check that Ollama service is accessible 
Using a browser, go to http://mini:11434/. It should show the message "Ollama is running"

##### 2. Run the Web UI for Ollama
We can use https://github.com/open-webui/open-webui as UI for Ollama
```shell
docker run -d -p 3000:8080 -e OLLAMA_BASE_URL=http://mini:11434 -v open-webui:/app/backend/data --name open-webui \
    --restart always ghcr.io/open-webui/open-webui:main
```
The web UI can be accessible at http://localhost:3000




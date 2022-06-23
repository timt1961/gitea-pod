# Running gitea in a podman pod

## Introduction

  There is a lot of literature about how to run gitea from a docker compose file. 
  However, for various reasons, I run podman on my pi, not docker. I needed a way to run gitea from a docker pod. 

  This repo contains a basic way of achieving that. It's not perhaps pretty, but it is fairly effective


## Files in this repo

- `docker-compose.yml` : the docker compose file I constructed using the getting started document in an earlier gitea document. 
- `start_pod` Construct a pod and add gitea and postgres to it


## How to work with this:

1. Run start_pod to start the pod
2. use `podman generate systemd --files --new --name gitea` to generate systemd files
3. copy the generated files to /home/ubuntu/.config/systemd/user
4. run `systemctl --user daemon-reload`
5. run `systemctl --user enable pod-gitea`
6. run `systemctl --user start pod-gitea`

Congrats: you now have a system that will survive a reboot
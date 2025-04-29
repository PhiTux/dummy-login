# Simple dummy login page

Just a simple dummy login page, with no further logic. Written in Svelte(kit). Just useful for demonstration purposes of sending username & password to the backend.

## Continue developing

- Install node 22

```bash
npm run dev
```

## Build docker image

```bash
docker build -t dummy-login .
```

Zip the image:

```bash
docker save -o dummy-login.zip dummy-login:latest

```

SCP it...

Load the image:

```bash
docker load -i dummy-login.zip
```

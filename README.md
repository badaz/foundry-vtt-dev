# Installation

## Install docker

Go to `https://docs.docker.com/engine/install/` and follow the instructions to install docker for your OS


## Install docker-compose

Go to `https://docs.docker.com/compose/install/` and install docker-compose

## Add secrets.json

Add a `secrets.json` file to the root of this project containing :

```JSON
{
  "foundry_admin_key": "admin",
  "foundry_username": "<your-foundry-vtt-username>",
  "foundry_password": "<your-foundry-vtt-password>"
}
```

Replace `foundry_username` and `foundry_password` with your foundry-vtt credentials. This will allow the created foundry instance to fetch your license key.

# Usage

Run

```BASH
docker-compose up -d
```

At first launch, Wait a moment for the foundry-vtt image to be pulled by docker, then wait for the container to download foundry and initialize.

You can follow what is going on inside the container by entering command

```BASH
docker logs -f shadowfoundry_foundry_1
```

Once the container is running and the foundry server has initialized, go to `127.0.0.1:30000` to find your running foundry instance. Enter your admin key and you're good to go!

In order to be able to modify the contents of the local data folder, you might have to make it writable using command
```
sudo chmod -R 777 data
```


# Info
 Inspired by https://github.com/felddy/foundryvtt-docker
 Foundry docker image and environment options : https://hub.docker.com/r/felddy/foundryvtt
Set up a sandboxed development environment for a foundry-vtt system, module or world in minutes!

# Installation

## Install docker

Go to https://docs.docker.com/engine/install/ and follow the instructions to install docker for your OS

## Install docker-compose

Go to https://docs.docker.com/compose/install/ and follow the instructions to install docker-compose for your OS
## Clone this repository and cd into it
```BASH
# by ssh
git clone git@github.com:badaz/foundry-vtt-dev.git && cd foundry-vtt-dev.git
# or http
git clone https://github.com/badaz/foundry-vtt-dev.git && cd foundry-vtt-dev.git
```

# Configuration

1. **Add secrets.json**

Add a `secrets.json` file to the root of this project containing :

```JSON
{
  "foundry_admin_key": "admin",
  "foundry_username": "<your-foundry-vtt-username>",
  "foundry_password": "<your-foundry-vtt-password>"
}
```

Replace `foundry_username` and `foundry_password` with your foundry-vtt credentials. This will allow the container to fetch your license key and download foundry.

2. **Create your system / module / world development folder**

> You must do this step before launching the container for the first time

> The folder name must match the system / module / world name


```BASH
mkdir data/Data/systems/<my-system-name>
# or
mkdir data/Data/modules/<my-module-name>
# or
mkdir data/Data/worlds/<my-world-name>
```

3. **Clone your system / module / world into the created folder**
```BASH
git clone https://github.com/<system-project-path> data/Data/systems/<my-system-name>/.
# or
git clone https://github.com/<module-project-path> data/Data/systems/<my-module-name>/.
# or
git clone https://github.com/<world-project-path> data/Data/systems/<my-world-name>/.
```

# Usage

Run

```BASH
docker-compose up -d
```

At first launch, please wait a moment for the foundry-vtt image to be pulled by docker, then wait for the container to download foundry and initialize.

You can follow what is going on inside the container by entering this command:

```BASH
docker-compose logs -f foundry
```

Once the container is running and the foundry server has initialized, go to `127.0.0.1:30000` to find your running foundry instance. Enter your admin key and you're good to go!

You may now start developing your system / module / world by editing the files in the previously created folder

# Troubleshooting

## Solve permission problems

If for some reason you did not create your system / module / world dev folder before launching the container, you will not have the file permissions to create it afterwards. However, you can force its creation with sudo and add correct owner afterward.


```BASH
sudo mkdir data/Data/systems/<my-system-name> && sudo chown $USER:$USER data/Data/systems/<my-system-name>
# or
mkdir data/Data/modules/<my-module-name> && sudo chown $USER:$USER data/Data/modules/<my-module-name>
# or
mkdir data/Data/worlds/<my-world-name> && sudo chown $USER:$USER data/Data/worlds/<my-world-name>
```

## OS other than Linux
Shell commands in this readme are bash commands. If using another OS or terminal program, please refer to their documentation to adapt the commands

# Info
 Inspired by https://github.com/felddy/foundryvtt-docker

 Foundry docker image and environment options : https://hub.docker.com/r/felddy/foundryvtt
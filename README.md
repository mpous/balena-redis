# Run Redis on a balena device

This is a guide to get started with Redis on a balena IoT device. Deploy it, run and experiment with the Redis server process and add it on your own fleet.

## Run it as a block

We maintain images for this block on balenaHub Container Registry. The images can be accessed using:

`bh.cr/marc6/redis<arch>` at the moment only available on `aarch64`.

For details on how to select a specific version or commit version of the image see our [documentation](https://www.balena.io/blog/improving-device-image-management-workflow-balenaHub-Container-Registry/).


## Getting started

### Hardware

* Raspberry Pi 4
* SD card 
* Power supply and (optionally) ethernet cable

### Software

* a balenaCloud account ([sign up here](https://dashboard.balena-cloud.com/))
* [Etcher](https://balena.io/etcher)

## Deploy as a balena Block

### docker-compose file

To use this image, create a container in your `docker-compose.yml` file as shown below:

```yaml
version: '2.1'
volumes:
  redis-data:
services:
    redis:
      image: redis                                                            
      volumes:                                                                               
        - redis-data:/data                                                                        
      restart: always    

```

## Deploy the code

### Via [Balena Deploy](https://www.balena.io/docs/learn/deploy/deploy-with-balena-button/)

Running this project is as simple as deploying it to a balenaCloud application. You can do it in just one click by using the button below:

[![](https://www.balena.io/deploy.png)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/mpous/redis-balena)

Follow instructions, click Add a Device and flash an SD card with that OS image dowloaded from balenaCloud. Enjoy the magic 🌟Over-The-Air🌟!


### Via [Balena-Cli](https://www.balena.io/docs/reference/balena-cli/)

If you are a balena CLI expert, feel free to use balena CLI.

- Sign up on [balena.io](https://dashboard.balena.io/signup)
- Create a new application on balenaCloud.
- Clone this repository to your local workspace.
- Using [Balena CLI](https://www.balena.io/docs/reference/cli/), push the code with `balena push <application-name>`
- See the magic happening, your device is getting updated 🌟Over-The-Air🌟!

## Run Redis on your Raspberry Pi

If Redis deployed properly you should see this on the balenaCloud logs.

![redis-balena-logs](https://user-images.githubusercontent.com/173156/163230933-2f99c0a2-4f2a-4b34-9369-b34577fdbd78.png)


### Get into the Redis CLI

Get into the `redis` container through the balenaCloud Terminal and type

`redis-cli`

![redis-balena-terminal-cli](https://user-images.githubusercontent.com/173156/163230987-eebd22c9-b215-4735-8f3e-6285734055d4.png)

The CLI from Redis might appear and from there you would be able to start working with Redis. Read more [here](https://redis.io/docs/getting-started/#exploring-redis-with-the-cli).

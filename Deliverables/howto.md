# How to run this application

This file has the following sections:

1. Setup
   - Pre-requisites
   - Docker installation
2. Scenario deployment
   - Composer use
3. Stop and remove the scenario

## Setup

Taking into account that the devs are using Mac OS as specified in the readme:

> may or may not have Docker (for Mac) installed.

### Pre-requisites

The user may need to install Docker first. You can skip this section if the following command on your terminal shows that you've Docker already installed. You can also look for a whale on your top status bar.

`docker -v`

Please, [notice that](https://docs.docker.com/docker-for-mac/install/):

1. Mac hardware must be a 2010 or newer model.
2. At least macOS El Capitan 10.11 is needed.
3. At least 4GB of RAM installed.
4. VirtualBox prior to version 4.3.30 must NOT be installed. Newer version is OK.

This could be checked using respectively, inside a terminal:

1. To check our hardware compatibility, it should support some hardware features:

`sysctl kern.hv_support`

2. To check our Mac OS version:

`sw_vers -productVersion`

3. From the Apple menu, select About This Mac. Click More Info, and then select the Memory tab to check.

4. Check if you have virtualbox installed, plus which version:

`virtualbox -v`

Remember to uninstall VirtualBox if its version is not compatible with Docker.

### Docker installation

Now we can install Docker.

1. Please start downloading it from [here](https://store.docker.com/editions/community/docker-ce-desktop-mac).

2. Run your `Docker.dmg` file in order to start the installation. Follow its indications to install it.

3. Once you've successfully installed Docker, start it. You'll be prompted to authorize it so the latest components can be installed.

4. Finally, check in the top status bar that Docker is running. A whale should be there while Docker is running.

## Scenario deployment

Now that we've Docker ready, just run `docker-compose` within the Deliverables folder (please, clone it completely. You can remove the `vendor` folder but then you have to run `composer` again for your app). With `-d` option we'll make it in background.

```
cd ./Deliverables
docker-compose up -d
```

This way, images will be build if necessary, then containers will be executed and your development environment will be ready.

### Composer use

To use composer, we invoke it each time that we need to generate a vendor. Go to your application folder on the host, and execute:

```
docker run --rm --interactive --tty     --volume $PWD:/app     --user $(id -u):$(id -g)     composer:latest install --ignore-platform-reqs --no-scripts
```

Parameters for this command includes non-root execution as `Composer` ask for, and `no scripts` options to avoid using some dependencies like git that are not available within the container.

## Stop and remove the scenario

To stop your environment just run:

`docker-compose stop`

And in order to remove the containers after they are stopped:

`docker-compose rm`

Please, notice that volumes attached to containers are not removed by default.

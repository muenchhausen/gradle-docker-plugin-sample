gradle-docker-plugin-sample DRAFT
=================================

a java hello world sample for the [gradle-docker-plugin] (https://github.com/bmuschko/gradle-docker-plugin) Version 0.71.
This hello world sample includes
* steps to setup first time boot2docker
* build docker image for a simple java application by gradle
* run the image

prepare boot2docker
-------------------
* Boot2docker must be installed. Here e.g. MAC OS, follow [docker installation mac] (https://docs.docker.com/installation/mac/).
* Start the boot2docker.app. It should be started, if not type in the console to start and show your env
    ```bash
    boot2docker up
    docker version
    boot2docker shellinit
    ```
* not sure - it might be required to set the following:
    ```bash
    boot2docker down
    VBoxManage modifyvm "boot2docker-vm" --natpf1 "tcp-port8080,tcp,,8080,,8080"
    boot2docker up
    ```

deactivate TLS in boot2docker
-----------------------------
run ```boot2docker ssh``` and inside
    ```bash
    sudo su -
    echo 'DOCKER_TLS=no' >> /var/lib/boot2docker/profile
    exit
    ```

get this java sample, build and run it
--------------------------------------
open a new console and run the following
```bash
git clone https://github.com/muenchhausen/gradle-docker-plugin-sample.git
cd gradle-docker-plugin-sample
gradle dockerBuildImage
```
if it is sucessful, run it:

```bash
docker run -d -p 8080:8080 31d5b1093bb8
```

open browser with the boot2docker IP address and Port 8080, e.g. http://192.168.59.103:8080/


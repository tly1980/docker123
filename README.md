## Slides


The slides can be found at [ http://slides.com/liyingtang/docker-123 ]( http://slides.com/liyingtang/docker-123 ).


## Demo 1. Get a taste of docker - Hello world

A really simple one, just try launch a ubuntu instance and create a file inside the instance.

1. Step 1: launch a container
```BASH
docker run -it ubuntu:14.04 bash
```

P.S.: 
> -i means interative - Keep stdin open
> -t means allocate a pseudo-TTY.
> Usually use "run -it <IMAGE_NAME_OR_VERSIONHASH> bash" when you need a interative shell. 
> It doesn't require bash, it could be other shell as well.


Because it is the first time you launch the instance, you're likely to get the following:
```BASH
Unable to find image 'ubuntu:14.04' locally
Pulling repository ubuntu
8251da35e7a7: Download complete
6071b4945dcf: Download complete
5bff21ba5409: Download complete
e5855facec0b: Download complete
Status: Downloaded newer image for ubuntu:14.04
```

Once it is finished, you will be in the BASH of that instance.

```
root@fb0169d4837c:/#
```

If you run:

```SHELL
$ docker ps
```

You will be getting something like
```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
bfd6e7796109        ubuntu:14.04        "bash"              7 seconds ago       Up 4 seconds                            hungry_pare
```

2. Step 2: create a file and commit

Inside the container, you run:
```
root@bfd6e7796109:/# echo "hello docker" > /hello.txt
```

Inside the host os, you run:
```
$ docker commit hungry_pare 'hellodocker'
192a0902a4a2c03e31cf48f836b997885c7ebc7aff7ab46c3b3f07aa96905ad5
```

Now you've already commited the changes of the container.
To verify that you can run ```docker images```.

```
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
hellodocker         latest              192a0902a4a2        6 seconds ago       188.4 MB
<none>              <none>              77a3c457c273        20 minutes ago      188.4 MB
ubuntu              trusty              8251da35e7a7        2 days ago          188.4 MB
...
...
```

From that you can see an docker image with ID ```192a0902a4a2``` has repository named ```hellodocker``` and tagged with ```latest```.


3. Step 3: Re-launch the image and verify the file.

You can either go ```docker run -it hellodocker bash``` or ```docker run -it 192a0902a4a2 bash```.

It will just create another container from image.

```
$ docker run -it hellodocker bash
root@9e1f2d441e81:/# cat /hello.txt
hello docker
```

4. Last but not least. Clean up your containers.

```docker ps``` will show you the active containers, namely those with a running process.

```docker ps -a``` willl show you all the containers, including those in-active one, namely with terminated process.

To my understanding, containers means un-wrapped images. 

Active one, means there is running process launched from the container, in-acvie one means there is no running process inside the containers.

To stop the active one, you will use ```docker kill <CONTAINER_ID>```.

For those in-active ones, you might want to remove the containers by using ```docker rm <CONTAINER_ID>```.


## Demo 2. Automating image baking: Dockerfile is your friend.

The magic is inside the ```Dockerfile``` and ```Makefile```





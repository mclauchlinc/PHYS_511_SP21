## PHYS 511 Nuclear Physics Coding Lab

This github repository will be fully ready by our class in April, but in the meantime it will serve as a guide on all the pre-class pieces we need to put together. Below is a guide on how to properly prepare yourself and your computer for our labs at that time

### Future Nuclear Physicsts

If you are planning on going into nuclear physics after this class, it is highly likely that you will encounter and use ROOT in the future. Therefore, I highly reccomend you do your work in this course with a ROOT focus. This will, unless you already have ROOT downloaded and compatible with Jupyter Notebooks, require you to download docker and work inside the container

### Not Future Nuclear Physicsts

If you don't plan on continuing in nuclar physics after this class, it is highly reccomended that you stick with the purely python route. You're far more likely to come into contact with python down the line as ROOT is pretty much exclusively used in nuclear physics.

Thus you have two paths before you:


#### Mac and Linux Users

You can either work inside the docker containers, or simply download conda and jupyter notebooks and work completely inside these frameworks, or download docker and work inside that container

#### Windows Users

I highly reccomend you work inside the docker container as we've run into many issues with trying to do otherwise in the past


## The Docker Path

-   [ ] Get [docker](#docker-install) installed and running :arrow_left: This is my recomendation if you're not familiar with programming or are using windows.

### Docker install

For windows computers I would suggest using docker. If installing for windows choose the linux images option not the windows images option.

-   Install for [Windows 10](https://docs.docker.com/docker-for-windows)
-   Install for [Windows 7](https://docs.docker.com/toolbox/toolbox_install_windows)
-   Install for [MacOS](https://docs.docker.com/docker-for-mac/install)

Docker is essentially a lightweight virtual machine called images. I have one of these images availbe with ROOT and python already installed in it for you.

First check that docker it working on your machine by running the hello-world image. In a terminal or command prompt window run this.

```bash
docker run --rm -it hello-world
```

If that doesn't work, email me and I'll try to help you get started.

If that works, great you're one more step to programming! Now run this command.

macOS/Linux users run:

```bash
docker run --rm -it -e USER="user" -p 9999:9999 -v $PWD:/home/user/data -w /home/user/data --entrypoint "jupyter" rootproject/root:6.22.06-conda notebook --allow-root --ip=0.0.0.0 --port=9999
```

For windows computers change USERNAME in "C:/Users/USERNAME" to your username and run.

```bash
docker run --rm -it -e USER="user" -p 9999:9999 -v $PWD:/home/user/data -w /home/user/data --entrypoint "jupyter" rootproject/root:6.22.06-conda notebook --allow-root --ip=0.0.0.0 --port=9999
```

If you have macOS/Linux add this to your rc file to get make a useful function.

```bash
jupyter-root () {
	docker run --rm -it \
        -e USER="user" -e DISPLAY=$DISPLAY \
        -e QT_X11_NO_MITSHM="1" \
        -p 9999:9999 \
        -v $PWD:/home/user/data \
        -v $HOME/.Xauthority:/home/user/.Xauthority \
        -w /home/user/data \
        -v /tmp/.X11-unix:/tmp/.X11-unix:rw \
        --entrypoint "jupyter" rootproject/root:6.22.06-conda notebook --allow-root --ip=0.0.0.0 --port=9999;
}
```
at which point you can run 

```bash
jupyter-root
```

in order to run the container, and access your jupyter notebook through the URL that pops up in your terminal

### Required Python Packages

First make sure you have python3.5 or newer. If not just use [docker](#docker-install).

```bash
python --version
```

To install the required packages.

```bash
pip3 install jupyter matplotlib numpy scipy pandas
```

## The Pure Python Path

-   [ ] Get [conda](#conda-install) installed and running
-   [ ] Get [jupyter notebooks](#jupyter-notebook-packages) and packages installed :arrow_left: If you're alreay familiar with python and have it on your computer

### Conda install

Documentation on installing conda for your operating system is located [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)

### Jupyter Notebook Install

Documentation on installing Jupyter Notebooks is located [here](https://jupyter.org/install)

## The ROOT C++ Path

If you would really prefer to work with C++ and ROOT, email me and we can work out a way to move forward with that as the setup will be, likely, more similar to how you'd work in the "real world" but will also require a bit more care in the setup

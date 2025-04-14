# RADIOCOSCON 2025 Hands-on sessions

## Docker 

To install Docker, click on [**here**](https://github.com/bbrawar/docker.git)

### Building the Docker Image
To build the Docker image from the provided Dockerfile, use the following command:

```sh
docker build -f Dockerfile -t oskar .
```
### List Docker Images
To view the images that have been built, use:
```sh
docker images
```

### Remove Docker Images
To remove an image, use:
```sh
docker rmi oskar
```

### Stop Docker Containers
To stop a running container, use:
```sh
docker stop container_id
```

## Running the Docker Container
After building the Docker image, you can run a container using:

```sh
docker run -it oskar
```

### Use Local Docker Image to make Signularity Container.
If you have a local Docker image and you want to use that to create your Singularity container:
```sh
docker save ddcal -o ddcal.tar
```

Use the docker-archive option to build the Singularity image:
```sh
singularity build ddcal.sif docker-archive://ddcal.tar
```
## Singularity Container

For install of Singularity container, click on [**here**](https://gitlab.com/samit-pal/singularity-containers.git)

### How to compile singularity on your created def file

```sh
sudo singularity build filename.sif name-of-your-file.def

e.g.

sudo singularity build wsclean.sif wsclean.def
or 
singularity build --fakeroot wsclean.sif wsclean.def

```
### Running the environment on your computer

```sh
singularity shell filename.sif

```
### Bind /scratch drive

in this case you have to **bind** the drive with singularity

```sh
singularity shell --bind /scratch:/scratch <path>/filename.sif

e.g.

singularity shell --bind /scratch/samit:/scratch/samit /home/samit/tools/filename.sif
```



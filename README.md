
![Docker Automated build](https://img.shields.io/docker/automated/jrottenberg/ffmpeg.svg)

## Standardized development environments Docker

Check the complete article at https://medium.com/@sandroathaide/working-effectively-with-code-a-development-environment-approach-6470de887d4d

## About docker

Please see the [Docker installation documentation](https://docs.docker.com/installation/) for details on how to upgrade your Docker daemon.

## How to use

All Dockerfiles specs are organized in folders by stack. 

In order to build the image, just run under your target stack

``
docker build --network=host -f Dockerfile -t image_name . 
``

When the image is available, just run

``
docker run --net=host -e DISPLAY=$DISPLAY -v /path_to_your_host_home_folder/:/home/developer -v /tmp/.X11-unix:/tmp/.X11-unix -it image_name
``

## Issues
If you have any problems with or questions about this image, please contact us through a [GitHub issue](https://github.com/sandroacoelho/docker-dev/issues).

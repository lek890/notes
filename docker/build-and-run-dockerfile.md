**Building docker image from the docker file**


Once we have a valid docker file, we can build them using `docker build -t` command.

We have to specify the name we need for the image and also the context in which the build should be done.

For ex: 
`docker build -t nginx-version2 .`

This command has to be run from the folder where the Dockerfile is available. Using `.` we are setting the
context.

Once the build is successful, we will have the image in our local. We can see it with the `docker images` command.

To run a docker image, use as usual

'docker run -d {CONTAINER_ID}'

The reason why I used the container id is that I didn't tag the image when I created it. Since I didn't tag
it, if I try to run using image name, say nginx-version2, docker will try to pull the image 'nginx-version2:latest'
and would fail as such an image is not available in the remote.

If you tag it correctly, you can simply run it with the image name.



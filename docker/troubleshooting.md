** Trouble shooting while running a container **

1.docker: Error response from daemon: OCI runtime create failed: container_linux.go:345: starting container process 
caused "exec: \"-p\": executable file not found in $PATH": unknown.

Solution: When running the image, the port mapping has to be specified before the image name/id. Otherwise
docker will try to execute the command after the image name on the container.

So, `docker run -d nginx-v2 -p 8080:90` is wrong

and

`docker run -d -p 8080:90 nginx-v2` is right.

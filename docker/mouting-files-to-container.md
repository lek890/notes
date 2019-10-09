**Mounting files to container**

While creating a container, we can tell docker to mount a local directory on the Docker host to a directory
on the container. 

An example is mounting nginx conf files. Nginx docker image uses default nginx configuration, there by setting
the root to `/usr/share/nginx/html` and the configuration files will be in `/etc/nginx`.

To upload new files from the Docker host to the above paths, we could do

`docker run -v /var/www:/usr/share/nginx/html:ro \ -v /var/nginx/conf:/etc/nginx:ro -P -d nginx`

Now changes in the Docker host on the above folders will reflect in the container folders. `ro` makes them 
readonly in the container.

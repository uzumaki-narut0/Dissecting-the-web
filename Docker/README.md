
What happens in `docker container run`
-------------------------------
* Looks for that image locally in image repository.
* Then looks in remote image repository (if it was not present locally, defaults to Docker Hub)
* Downloads the latest version (nginx:latest by default)
* Creates a new Container based on that image and prepares to start.
* Gives it a virtual IP on a private network inside Docker Engine.
* Opens up port 80 on host and forwards to port 80 on Container.
* Starts Container by using the CMD in the image Dockerfile.

***

`docker top [container name]` : List running processes in a specific Container

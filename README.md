# Continuous Integration assignment 1
Build, Run and test Python Flask app.

### Trigger
This workflows actions will run on push or pull requests.

### Docker Pull - Download the docker Image from repository.

```
run: docker pull lvthillo/python-flask-docker
```

### Run the container and listen to port 8080.

```
run: docker run --name my-container -d -p 8080:8080 lvthillo/python-flask-docker
```

### Build the Docker image - install all dependencies from a docker file.
```
run: docker build . --file Dockerfile 
```

### Test if App is running (Curl)
I used curl command that display a web page with the host name an ip address.
```
run: curl http://localhost:8080/
```

### I verify that the ip is the same as the running container ip.
```
run: docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-container
```
This command display the ip address of the docer that is the same as the app web page shows.

### I verify the host name that is the same as the running container host name.
```
run: docker inspect -f '{{ .Config.Hostname }}' my-container
```

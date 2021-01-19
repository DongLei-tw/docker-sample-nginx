# docker-sample-nginx
a sample nginx container to display container name


### Docker Build 

```bash
$ docker build -t my-app:latest .
```

```bash
$ docker build -f path/to/Dockefile -t my-app:latest .
```

### Run 

```bash
$ docker run --rm --name my-server -p 80:80 my-nginx:latest
```
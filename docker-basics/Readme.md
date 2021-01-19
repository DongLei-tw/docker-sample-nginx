# Docke Run 


```bash
$ docker run -d -p 80:80 docker/getting-started
```

```bash
$ docker run -it -v {absolute/path/to/file}:{path/in/container} ImageNmae:Tag /bin/bash
```

例如

```bash 
$ docke run -it -v ~/workspace/docker-run/config.json:/1.json ubuntu /bin/bash
```
# Docker Compose 


### Docker compose 文件

```yaml

# Docker-compose file format verison, 需要与你的docker engine版本相匹配.
version: "3.9" 

# 服务，主要用来整合容器，表明他们之前的关系
services:
  # 二级标签是 web，用户自定义名称，它就是服务名称
  web:
    # 基于一份Dockerfile，在使用 up 启动之时执行构建任务，
    # 这个构建标签就是 build，它可以指定 Dockerfile 所在文件夹的路径
    # 这里就是找当前文件夹
    build: .
    # 容器的依赖、启动先后的问题，先启动依赖
    # depends_on: redis
    # 端口映射
    ports:
      - "5000:5000"
    # 文件挂载
    volumes:
      - .:/code
    # 容器使用的环境变量
    environment:
      FLASK_ENV: development
  # 另外一个服务
  redis:
    image: "redis:alpine"
```

### Network

[官方文档](https://docs.docker.com/compose/networking/)

`docker-compose up` 会创建一个默认网络叫做 `myapp_default`, 默认配置下所有的服务都被加入到了这个网络下。

```yaml
version: "3"
services:

  proxy:
    build: ./proxy
    # 本服务所在的网络
    networks:
      - frontend
  app:
    build: ./app
    # 可以给一个服务指定多个网络
    networks:
      - frontend
      - backend
  db:
    image: postgres
    networks:
      - backend

# 定义网络
networks:
  frontend:
    # Use a custom driver
    driver: custom-driver-1
  backend:
    # Use a custom driver which takes special options
    driver: custom-driver-2
    driver_opts:
      foo: "1"
      bar: "2"
```

### Docker Compose 命令

常用命令：

|命令| 说明 |
|:--:|:----|
| build | Build or rebuild services |
| up | Create and start containers|
| down | Stop and remove containers, networks, images, and volumes
|




```bash
$ docker-compose up
```

[更多命令](https://docs.docker.com/compose/reference/overview/)


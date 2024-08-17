# reverse-image-search

基于 https://github.com/hetao29/reverse_image_search 的 Docker构建，方便部署和安装

可以参考docker-compose.yml的部署，配置文件可以参考config.py，方便错误定位

Docker的配置文件
```yml
services:
  search:
    image: hetao29/reverse-image-search:latest
    volumes:
      - data_root:/root
    ports:
      - "5000:5000"
    configs:
      - source: conf
        target: /app/reverse_image_search/server/config.py
volumes:
  data_root:
    driver: local
    driver_opts:
      type: none
      o: bind
      device: /data/milvus/data/root/
configs:
  conf:
    file: ./config.py
```

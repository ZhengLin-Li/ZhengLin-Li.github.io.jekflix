

https://stonedb.io/docs/getting-started/quick-deploy-in-docker

```
docker pull stoneatom/stonedb
docker run -p 3306:3306 -itd  -e MYSQL_ROOT_PASSWORD='123456'  stoneatom/stonedb
docker ps
docker exec -it <Container ID> bash
/opt/stonedb57/install/bin/mysql -uroot -p123456
```

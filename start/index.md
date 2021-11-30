### docker-manager

```
docker pull xiaojun207/docker-manager:1.0.5

docker ps -aq --filter "name=docker-manager" | grep -q . && docker stop docker-manager && docker rm -fv docker-manager

docker run -d --name docker-manager -p 8068:8068 -e driveName=mysql -e dataSourceUrl='root:Abc123@(dbhost:3306)/dbname?charset=utf8' xiaojun207/docker-manager:1.0.5

```

Parameter Description:

Parameter | required | default value | description
---|----------|-------|--- 
dataSourceUrl | required | -     | database connection URL, such as：-e dataSourceUrl='root:Abc123@(dbhost:3306)/dbname?charset=utf8'
driveName | no       | mysql | Defaults to MySQL. Other database support will be considered later
useCache | no       | false | whether to enable local cache. It can be enabled in stand-alone deployment, but not in cluster deployment


### docker-agent

```
docker pull xiaojun207/docker-agent:latest

docker run -d --name docker-agent -v /var/run/docker.sock:/var/run/docker.sock -e DockerServer="http://192.168.1.200:8068/dockerMgrApi" -e Token="12345678" xiaojun207/docker-agent:latest

```
It should be used in conjunction with "xiaojun207/docker-agent" image. Please refer to the description for the specific usage of docker agent

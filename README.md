# APIGateDemo.Ocelot
#
#
#
# Delete all containers
docker rm $(docker ps -a -q)
# Delete all images
docker rmi $(docker images -q)

docker stop $(docker ps -aq)
 docker rm $(docker ps -a -q) remove none tag docker
 docker run -d -p 1433:1433 -e sa_password=<SA_PASSWORD> -e ACCEPT_EULA=Y microsoft/mssql-server-windows-developer

docker inspect --format="{{range .NetworkSettings.Networks}}{{.IPAddress}} {{end}}" a77a722d2268

docker run -i --expose=22 b5593e60c33b bash
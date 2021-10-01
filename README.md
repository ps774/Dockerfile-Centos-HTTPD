# Dockerfile-Image
#In a jenkins job, we can Build-image and Run-container using Publish over SSH plugin
#These are the commands we have to run in Exec commond block

cd ~/Docker
docker image prune -a -f
docker build -t myimg:${BUILD_NUMBER} .
docker rm -f web1
docker run -dit -p 8081:80 --name web1 myimg:${BUILD_NUMBER}

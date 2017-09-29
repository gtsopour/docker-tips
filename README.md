# Collection of Docker Commands
[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

## Generic
**Connect to running container**  
`$ docker exec -it "CONTAINER_ID" /bin/bash`

**Launch single container**  
`$ docker run --name=NAME --env-file="ENV_FILE" -it "IMAGE_NAME" /bin/bash`

**List all containers**  
`$ docker ps -a`

**List all images**  
`$ docker images`

**Delete local image**  
`$ docker rmi <IMAGE_ID>`

**Delete all image versions**  
`$ docker rmi -f $(docker images IMAGE_NAME -q -a)`

**Delete all untagged images**  
`$ docker rmi $(docker images | grep "^<none>" | awk '{ print $3 }')`

**Push image to shared repo**  
`$ docker rmi $(docker images | grep "^<none>" | awk '{ print $3 }')`
`$ docker rmi $(docker images | grep "^<none>" | awk '{ print $3 }')`

## NPM
**NPM scripts example**
`"scripts": {
  "docker:build": "npm run build && docker build -t IMAGE_NAME:latest .",
  "docker:deploy": "npm run docker:build && docker tag IMAGE_NAME:latest $npm_config_repo/IMAGE_NAME:$npm_package_version && docker push $npm_config_repo/IMAGE_NAME:$npm_package_version",
   "docker:run": "docker run -i -t IMAGE_NAME:$npm_package_version"
}`

## Docker

Download and modify a Docker image:

```
docker images
docker run -t -i ruby:2.3 /bin/bash

$ apt-get update
$ apt-get install nodejs -y
$ gem install bundler --no-ri --no-rdoc
# A Dockerfile is a great option for the following line or
# maybe integrate with our current CI script?
$ bundle install
$ exit

# Log back in?
docker ps -a # and get container sha
docker start -i <container-sha>
```

----------
## Create a custom image

```
# Commit a new image
docker commit -m "Adds dependencies" -a "Peter Parker" \
<container-sha> registry.gitlab.com/<group-name>/projectname:v2

# Or commit the image and tag it later
docker tag <image id> <url>:<port>/<user/project>:<tag>

# Login in to GitLab registry
# docker login registry.gitlab.com
docker login <url>:<port>

# Push image to registry
# docker push registry.gitlab.com/gitlab-org/ci-training-sample
docker push <registry-url>/<group-name>/<project-name>:<tag>
```

[Back](#/agenda)

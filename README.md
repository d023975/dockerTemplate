# dockerTemplate

## Docker cli, server, registry
- https://docs.docker.com/install/
- server dockerd
- cli docker
- docker registry to hold images
  - https://docs.docker.com/registry/
    - docker run -d -p 5000:5000 --restart=always --name registry registry:2
  - https://docs.docker.com/registry/introduction/
  - docker pull, docker push
  - The Registry is open-source, under the permissive Apache license.
  - docker pull ubuntu instructs docker to pull an image named ubuntu from the official Docker Hub. This is simply a shortcut for the longer docker pull docker.io/library/ubuntu command
  - https://docs.docker.com/registry/deploying/



## Use Case

Running your own Registry is a great solution to integrate with and complement your CI/CD system. In a typical workflow, a commit to your source revision control system would trigger a build on your CI system, which would then push a new image to your Registry if the build is successful. A notification from the Registry would then trigger a deployment on a staging environment, or notify other systems that a new image is available.

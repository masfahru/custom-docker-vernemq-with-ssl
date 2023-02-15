# Custom Docker VerneMQ with Secure Websocket (WSS)

You should build your own VerneMQ docker image and push it to docker hub, you can check the official Docker VerneMQ: https://github.com/vernemq/docker-vernemq.

Using that official Docker VerneMQ, i am unable to enable secure websocket (wss) using Dockerfile, but it can be enabled using Helm package manager: https://github.com/vernemq/docker-vernemq/blob/148c27a245d5cdbe7a62c54db9b9e8c247a873f8/helm/vernemq/templates/statefulset.yaml#L84. Since i don't want to use Helm, i have modified the Docker VerneMQ scripts to enable wss automatically when server certificates are provided, i have pushed the output image to Docker hub: https://hub.docker.com/repository/docker/imamfahrurrofi/vernemq/general. The environment should be the same with the official Docker VerneMQ, except i don't have to accept eula (env `DOCKER_VERNEMQ_ACCEPT_EULA` is not required). 

In this repository, i provide a Dockerfile which use the custom Docker image. To enable secure websockets (wss), you have to provide env `DOCKER_VERNEMQ_LISTENER__WSS__CAFILE`, `DOCKER_VERNEMQ_LISTENER__WSS__CERTFILE`, `DOCKER_VERNEMQ_LISTENER__WSS__KEYFILE` in Dockerfile and their respective certificates in folder ssl. There is an example of file based access control list (vmq.acl) for you to test.

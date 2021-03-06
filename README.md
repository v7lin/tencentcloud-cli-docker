# tencentcloud-cli-docker

[![Build Status](https://cloud.drone.io/api/badges/v7lin/tencentcloud-cli-docker/status.svg)](https://cloud.drone.io/v7lin/tencentcloud-cli-docker)
[![Docker Pulls](https://img.shields.io/docker/pulls/v7lin/tencentcloud-cli.svg)](https://hub.docker.com/r/v7lin/tencentcloud-cli)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/v7lin/tencentcloud-cli-docker/blob/master/LICENSE)

### 项目源码

[tencentcloud-cli](https://github.com/TencentCloud/tencentcloud-cli)

### 腾讯云控制台

[访问管理](https://console.cloud.tencent.com/cam/capi)

### usage

* docker

````
docker run --rm -it v7lin/tencentcloud-cli sh -c "tccli version"
docker run --rm -it -v ${PWD}/.tccli:/root/.tccli v7lin/tencentcloud-cli sh -c "tccli configure"
docker run --rm -it -v ${PWD}/.tccli:/root/.tccli v7lin/tencentcloud-cli sh -c "tccli configure set secretId ${TENCENT_SECRET_ID} secretKey ${TENCENT_SECRET_KEY} region ${TENCENT_REGION} output json && tccli configure list"
docker run --rm -it -v ${PWD}/.tccli:/root/.tccli v7lin/tencentcloud-cli sh -c "tccli configure list"
````

* drone

````
- name: tencentcloud-cli
  image: v7lin/tencentcloud-cli
  environment:
    TENCENT_SECRET_ID:
      from_secret: TENCENT_SECRET_ID
    TENCENT_SECRET_KEY:
      from_secret: TENCENT_SECRET_KEY
    TENCENT_REGION:
      from_secret: TENCENT_REGION
  commands:
  - tccli configure set secretId $TENCENT_SECRET_ID secretKey $TENCENT_SECRET_KEY region $TENCENT_REGION output json
  - tccli configure list
````

# Pushing Github "node js webserver as docker" to Amazon Elastic Container Registry

![alt text](https://github.com/ioctlsg/simonongcloudnative/blob/main/Screenshot%202023-07-18%20at%209.45.37%20PM.png)




```
Mac-mini:simonongcloudnative simonsoul$ aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin **********.dkr.ecr.ap-southeast-1.amazonaws.com
Login Succeeded

Logging in with your password grants your terminal complete access to your account. 
For better security, log in with a limited-privilege personal access token. Learn more at https://docs.docker.com/go/access-tokens/
Mac-mini:simonongcloudnative simonsoul$ docker push ****************.dkr.ecr.ap-southeast-1.amazonaws.com/simonongcloudnative:latest
The push refers to repository [255945442255.dkr.ecr.ap-southeast-1.amazonaws.com/simonongcloudnative]
ad8527a6e34e: Pushed 
69de70f99b9a: Pushed 
ead2512d59d2: Pushed 
fe5e54eddfe0: Pushed 
0f3e297c6df7: Pushed 
77f609faa0a8: Pushed 
c62e3218b67b: Pushed 
61f2871f545a: Pushed 
latest: digest: sha256:655e9fce471daaf730559e481960be8e53bfce835866d214a7ea5be82a90ab33 size: 1994
Mac-mini:simonongcloudnative simonsoul$ npm install

up to date, audited 59 packages in 472ms

8 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
Mac-mini:simonongcloudnative simonsoul$ docker build -t simonongcloudnative .
[+] Building 2.1s (11/11) FINISHED                                                                      docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                    0.0s
 => => transferring dockerfile: 459B                                                                                    0.0s
 => [internal] load .dockerignore                                                                                       0.0s
 => => transferring context: 2B                                                                                         0.0s
 => [internal] load metadata for docker.io/library/node:16-alpine                                                       1.9s
 => [auth] library/node:pull token for registry-1.docker.io                                                             0.0s
 => [1/5] FROM docker.io/library/node:16-alpine@sha256:6c381d5dc2a11dcdb693f0301e8587e43f440c90cdb8933eaaaabb905d44cdb  0.0s
 => [internal] load build context                                                                                       0.1s
 => => transferring context: 151.47kB                                                                                   0.1s
 => CACHED [2/5] WORKDIR /my-app                                                                                        0.0s
 => CACHED [3/5] COPY package*.json ./                                                                                  0.0s
 => CACHED [4/5] RUN npm install                                                                                        0.0s
 => [5/5] COPY . .                                                                                                      0.1s
 => exporting to image                                                                                                  0.1s
 => => exporting layers                                                                                                 0.1s
 => => writing image sha256:5f815db95b5409cd29d5f8842d731634f1faaf47ebe255cc3536a13bedb13933                            0.0s
 => => naming to docker.io/library/simonongcloudnative                                                                  0.0s

What's Next?
  View summary of image vulnerabilities and recommendations → docker scout quickview
Mac-mini:simonongcloudnative simonsoul$ docker tag simonongcloudnative:latest *************.dkr.ecr.ap-southeast-1.amazonaws.com/simonongcloudnative:latest
Mac-mini:simonongcloudnative simonsoul$ docker push ************.dkr.ecr.ap-southeast-1.amazonaws.com/simonongcloudnative:latest
The push refers to repository [*************.dkr.ecr.ap-southeast-1.amazonaws.com/simonongcloudnative]
9e8a62775dc2: Pushed 
69de70f99b9a: Layer already exists 
ead2512d59d2: Layer already exists 
fe5e54eddfe0: Layer already exists 
0f3e297c6df7: Layer already exists 
77f609faa0a8: Layer already exists 
c62e3218b67b: Layer already exists 
61f2871f545a: Layer already exists 
latest: digest: sha256:dd631a74da3f6cbeb8a4ad7cbf21a5ec2c61b3c3c0bbd6f0723f0b5e1c414944 size: 1994
Mac-mini:simonongcloudnative simonsoul$ git add .
Mac-mini:simonongcloudnative simonsoul$ git commit -m "push to AWS"
[main 14c4b59] push to AWS
 10 files changed, 37 insertions(+), 8 deletions(-)
 delete mode 100755 .Dockerfile.icloud
 delete mode 100755 .README.md.icloud
 delete mode 100755 .package.json.icloud
 create mode 100755 Dockerfile
 create mode 100755 README.md
 delete mode 100644 package 2.json
 create mode 100755 package.json
Mac-mini:simonongcloudnative simonsoul$ git push
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 8 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (9/9), 1.08 KiB | 1.08 MiB/s, done.
Total 9 (delta 4), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (4/4), completed with 3 local objects.
To github.com:ioctlsg/simonongcloudnative.git
   47dd5d9..14c4b59  main -> main
Mac-mini:simonongcloudnative simonsoul$

```

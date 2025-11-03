# for public image

https://github.com/users/uynuraw/packages/container/package/mypublic

## list of image
openmaxio for arm64
- [ghcr.io/uynuraw/mypublic:openmaxio-v1.7.6-arm64](https://github.com/users/uynuraw/packages/container/mypublic/559064904?tag=openmaxio-v1.7.6-arm64)

kafka client (kafka-sh, kcat, rpk, curl(for connectors api))
- [ghcr.io/uynuraw/mypublic:my-kafka-v1.0](https://github.com/users/uynuraw/packages/container/mypublic/561911079?tag=my-kafka-v1.0)

## วิธีทำ
1. สร้าง repo แบบ public
2. push image
3. config package setting ให้เป็น public
   1. https://github.com/users/uynuraw/packages/container/mypublic/settings
4. pull image ได้เลยไม่ต้อง login

## remark
gitlab ทำ pull image public ไม่ได้ ต้องผ่านการ access login ก่อน  
Container registry set ได้แค่ private , everyone with access  
https://gitlab.com/yuuplay/mypublic/edit#js-shared-permissions

## example
```sh
# step 0 login registry/package ต้อง login ถึงจะ push ได้ ไม่เกี่ยวกับ pull
# for github
docker login ghcr.io
# for gitlab
docker login registry.gitlab.com

# step 1 build image
# build for github
docker build -t ghcr.io/uynuraw/mypublic:openmaxio-v1.7.6-arm64 .
# build for gitlab
docker build -t registry.gitlab.com/yuuplay/mypublic:openmaxio-v1.7.6-arm64 .
# build for local แล้วสร้าง tag ใหม่สำหรับ github
docker build -t openmaxio-console:v1.7.6-arm64 .
docker tag openmaxio-console:v1.7.6-arm64 ghcr.io/uynuraw/mypublic:openmaxio-v1.7.6-arm64

# step 2 push image
# for github
docker push ghcr.io/uynuraw/mypublic:openmaxio-v1.7.6-arm64
# for gitlab
docker push registry.gitlab.com/yuuplay/mypublic:openmaxio-v1.7.6-arm64

```

## remark
- Metered usage (https://github.com/settings/billing)
- package แบบ public จะไม่คิด quota 
- package แบบ private (free) จะมี storage 500 MB , data transfer 1GB (https://github.com/settings/billing )
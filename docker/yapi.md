### 构建yapi镜像

#### 1、下载 YAPI 到本地
    wget https://github.com/YMFE/yapi/archive/v1.9.2.tar.gz
    tar -zxvf v1.9.2.tar.gz && cd yapi-1.9.2
    
#### 2、编辑 Dockerfile
    FROM node:12-alpine as builder
        
    RUN apk add --no-cache git python make openssl tar gcc
        
    RUN cd /api/vendors && \
        npm install --production --registry https://registry.npm.taobao.org
        
    FROM node:12-alpine
        
    MAINTAINER 2865900737@qq.com
        
    ENV TZ="Asia/Shanghai" HOME="/"
        
    WORKDIR ${HOME}
        
    COPY --from=builder ./ /api/vendors
        
    COPY config.json /api/
        
    EXPOSE 3000
        
    ENTRYPOINT ["node"]
    
#### 3、构建镜像
    docker build -t yapi .

#### 启动 Yapi 服务

    # 1、停止并删除旧版容器
    docker rm -f yapi
    
    # 3、启动新容器
    docker run -d \
      --name yapi \
      --link mongo:mongo \
      --workdir /api/vendors \
      -p 3000:3000 \
      yapi \
      server/app.js
    
### 构建yapi镜像

#### 1、下载 YAPI 到本地
    wget https://github.com/YMFE/yapi/archive/v1.9.2.tar.gz
    
### 2、安装node
    https://www.jianshu.com/p/fa18c80fd55c
    
    1) 可视化部署[推荐]
    
    npm install -g yapi-cli --registry https://registry.npm.taobao.org
    yapi server
    
    2) 配置mongo
    use yapi
    db.createUser({ user: 'yapi', pwd: 'RnOiNEUDmluUjGPT', roles: [ { role: "readWrite", db: "yapi" } ] })
    db.auth("yapi", "RnOiNEUDmluUjGPT")
    
    3) 安装初始化
    
    初始化管理员账号成功,账号名："2860900737@qq.com"，密码："ymfe.org"
    部署成功，请切换到部署目录，输入： "node vendors/server/app.js" 指令启动服务器, 然后在浏览器打开 http://127.0.0.1:3000 访问
    
    4) 启动yapi
       
    cd /usr/local/src/node/lib/node_modules/yapi-cli/src/commands/my-yapi
    node vendors/server/app.js
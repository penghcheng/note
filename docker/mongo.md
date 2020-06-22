### Mongo 创建
    docker run -d -p 27017:27017 -v /data/mongodb/configdb:/data/configdb -v /data/mongodb/db:/data/db --name mongo docker.io/mongo --auth
    
    mongo
    use admin
    db.createUser({ user: 'admin', pwd: 'RnOiNEUDmluUjGPT', roles: [ { role: "root", db: "admin" } ] })
    
    db.auth("admin", "RnOiNEUDmluUjGPT")
    
    use yapi
    db.createUser({ user: 'yapi', pwd: 'RnOiNEUDmluUjGPT', roles: [ { role: "readWrite", db: "yapi" } ] })
    
    db.auth("yapi", "RnOiNEUDmluUjGPT")
    
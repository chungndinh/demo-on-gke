kubectl create secret generic demo-db-secret --from-literal=DB_USER=myuser --from-literal=DB_PASSWORD=myuserpass
        envFrom:      
        - secretRef:
            name: postgres-test-secret
kubectl create secret generic demo-redis-secret --from-literal=REDIS_PASSWORD=redispass
File bash script phải được tab
Trong docker thêm command để kiểm tra kết nối tới redis
apk --update add redis 

redis-cli -h demo-redis-service -p 6379 -a redispass
# Test scale hpa by request CPU
kubectl run -it --rm --restart=Never loadgenerator --image=busybox -- sh -c "while true; do wget -O - -q https://motthang.ga; done"
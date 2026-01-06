# edu zookeeper-StatefulSet

بعد از اجرا : 
```
kubectl apply -f zookeeper-statefulset.yaml
```
3️⃣ بررسی وضعیت
```
kubectl get pods -l app=zookeeper
```

```
zookeeper-0   Running
zookeeper-1   Running
zookeeper-2   Running
```
4️⃣ تست quorum ZooKeeper
اتصال به ZooKeeper:
```
kubectl exec -it zookeeper-0 -- zkCli.sh
```
بررسی وضعیت نود:
```
echo ruok | nc zookeeper-0.zookeeper 2181
```
خروجی سالم:

```
imok
```
5️⃣ نکات حرفه‌ای / مصاحبه‌ای 🔥
مورد	توضیح
```
StatefulSet	identity ثابت برای quorum
Headless Service	discovery داخلی
Odd nodes	quorum همیشه لازم
PVC	جلوگیری از data loss
Ports 2888/3888	leader election
```
6️⃣ منابع پیشنهادی
Resource	مقدار
CPU	0.5 core
RAM	1GB
Disk	5GB × 3

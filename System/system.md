#VPS
## Out of memory
Если не хватает оперативной памяти то можно создать файл подкачки
```
#Вывести информацию о доступной памяти
free -m
```
```
#Вывести информацию о доступной памяти на диске
df -h -t ext4
```
Cоздаем файл подкачки размером 2G
```
mkdir -p /var/_swap_
cd /var/_swap_
#Here, 1M * 2000 ~= 2GB of swap memory
dd if=/dev/zero of=swapfile bs=1M count=2000
mkswap swapfile
swapon swapfile
chmod 600 swapfile
echo "/var/_swap_/swapfile none swap sw 0 0" >> /etc/fstab
```
Отключаем файл подкачки 
```
swapoff /var/_swap_/swapfile
```
# Домашнее задание к занятию «Защита хоста»
sys-37 Пономарев Игорь
### Задание 1

1. Установите **eCryptfs**.
2. Добавьте пользователя cryptouser.
3. Зашифруйте домашний каталог пользователя с помощью eCryptfs.

*В качестве ответа  пришлите снимки экрана домашнего каталога пользователя с исходными и зашифрованными данными.*

**Решение 1:**

1. Установим **ecryptfs** в ВМ :
```
apt install ecryptfs-utils cryptsetup -y
```
2. Добавим пользователя **cryptouser**:
```
sudo adduser cryptouser
su - cryptouser
```
</kbd> ![image](https://github.com/user-attachments/assets/a651da38-5eca-425b-a64b-311d5a503e6b)

3. Зашифруйте домашний каталог пользователя **/home/cryptouser** с помощью **eCryptfs**:

Посмотрим содержимое еще не зашифрованной домашней директории пользователя:
![image](https://github.com/user-attachments/assets/b5fd17bf-e38f-43ef-9b98-9666d1cfd0e3)


- Зашифруем содержимое каталога:
```
sudo ecryptfs-migrate-home -u cryptouser
sudo ls -la /home/cryptouser
```
![image](https://github.com/user-attachments/assets/c5201007-9342-4820-b560-5bfc2c31222e)
---

```
sudo ls -la /home/cryptouser
```
![image](https://github.com/user-attachments/assets/fd2b8498-37b9-455e-beed-3512e1c2f87a)


### Задание 2

1. Установите поддержку **LUKS**.
2. Создайте небольшой раздел, например, 100 Мб.
3. Зашифруйте созданный раздел с помощью LUKS.

*В качестве ответа пришлите снимки экрана с поэтапным выполнением задания.*

**Решение 2:**

1. Установим поддержку **luks**:
```
sudo apt install cryptsetup lvm2
```
![image](https://github.com/user-attachments/assets/2a501227-a32e-431e-9238-449c38d8221c)
![image](https://github.com/user-attachments/assets/9d723f55-c016-4278-9887-498dfa3f4940)

2. Создадим новый раздел размером 100 МБ :
```
dd if=/dev/zero of=testdisk.img bs=1M count=100
```
![image](https://github.com/user-attachments/assets/c85daa2a-685b-49d5-8db5-b258d145fff3)
![image](https://github.com/user-attachments/assets/ced2d574-5bbf-47b1-b773-3f2ff666157f)
```

3. Зашифруйте созданный раздел:

```
![image](https://github.com/user-attachments/assets/232e4f06-b53d-48a3-9bb9-3dc195c9be61)
```

- Смонтируем раздел:
```
![image](https://github.com/user-attachments/assets/4379cfd8-e93c-4e54-ac76-c029fce88efc)

```

- Отформатируем раздел:
```
![image](https://github.com/user-attachments/assets/6ec57949-6fdb-4532-a705-c653247ae1de)

```


- Монтирование открытого раздела:
```
![image](https://github.com/user-attachments/assets/c08f8ba0-a4f5-46fa-b6c1-5232f1d5713e)

```


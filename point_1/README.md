## Настройка vm-app
ОСЬ: Ubuntu Server 22.04
Имя: VM-app
ОЗУ: 2Gb
ПЗУ: 25Gb
Адаптер: NAT

Проброшенные порты:
SSH     TCP         2222        22


### Настройка sshd

1. Проверил доступность сервиса командой 
    ```
    sudo systemctl status ssh
    ```
2. Загенерил ssh-ключпару
    ``` 
    ssh-keygen -t rsa -b 4096 
    ```

3. Закинул pab ключ на виртуалку    
    ``` 
    type C:\Users\user\.ssh\id_rsa.pub | ssh user@localhost -p 2222 "cat >> ~/.ssh/authorized_keys"     
    ```

3. После проверки, залез в /etc/ssh/sshd_config и закинул параметры:
 
    ```
    PasswordAuthentication no
    PermitRootLogin no
    PubkeyAuthentication yes
    ```
4. Ребутнул сервис ssh

    ``` 
    sudo systemctl restart ssh 
    ```
5. Подключение к вертуалке

    ```
    ssh -p 2222 user@127.0.0.1
    ```

### Настройка контейнеров
[Доки по установке докера на убунту](https://docs.docker.com/engine/install/ubuntu/)
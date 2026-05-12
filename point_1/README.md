### Настройка vm-app

1. Поднял вмку в VirtualBox, образ поднялся c базовыми конфигурациями сети. 
2. Настроил ссш доступ в вмку, поднял фаервол для проброса 22 порта 


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

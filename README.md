В inventory моенять ip на свой
1. Подготовка Control VM (первая ВМ)
```
# Установка Ansible
sudo apt update
sudo apt install -y ansible

# Создание пользователя ansible-user
sudo useradd -m -s /bin/bash ansible-user
sudo usermod -aG sudo ansible-user

# Генерация SSH-ключа
sudo -u ansible-user ssh-keygen -t ed25519 -f /home/ansible-user/.ssh/id_ed25519 -N ""
```
2. Настройка пользователя на обеих ВМ
На Control VM (выполните локально):
```
# Копирование ключа на вторую ВМ (замените <IP> на реальный IP)
sudo -u ansible-user ssh-copy-id -i /home/ansible-user/.ssh/id_ed25519 ansible-user@<IP_второй_ВМ>
```

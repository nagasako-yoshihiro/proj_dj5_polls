https://github.com/conda-forge/miniforge
$ conda create --name django python=3.12
$ conda activate django
$ conda install Django mysqlclient mysql-client gettext

########
for Docker
########
$ sudo usermod -aG docker $USER
$ grep docker /etc/group
docker:x:124:snaf

Debian 12 では不要。
$ sudo apt install docker-buildx

#----
$ docker-compose up -d
or
$ podman compose up -d
########

localhost:8080 -> phpmyadmin
$ mysql -u user -p -h 127.0.0.1

=== docker/db/initdb.d/polls.sql を作成し、修正する。
$ mysqldump --user=root -p --host=127.0.0.1 polls \
  --skip-column-statistics --lock-tables=0 > docker/db/initdb.d/polls.sql

$ mysql -u root -p -h 127.0.0.1 < docker/db/initdb.d/polls.sql

=== Docker on Manjaro ===
## Update
sudo pacman -Syu

## インストール
sudo pacman -S docker docker-compose

## 起動する
sudo systemctl start docker.service

## 自動起動設定
sudo systemctl enable docker.service

## User Group
sudo usermod -aG docker $USER

## reboot

## buildx
sudo pacman -S docker-buildx
docker buildx install

=== 多言語化 ===
django-admin makemessages -l ja
django-admin makemessages -l en
django-admin makemessages -l de
django-admin makemessages -l fr
django-admin makemessages -l ko
django-admin makemessages -l zh_Hans
django-admin makemessages -l zh_Hant
django-admin makemessages -l vi
...
修正の時は --all
django-admin makemessages --all
翻訳文字列セットしてからコンパイルする
django-admin compilemessages

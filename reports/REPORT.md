# Лабораторная работа №13. Отчет.

## Задание на лабораторную работу:

- [x] 1. Создать публичный репозиторий с названием **lab13** на сервисе **GitHub**
- [x] 2. Выполнить инструкцию учебного материала
- [x] 3. Ознакомиться со ссылками учебного материала
- [x] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Выполнение работы.
	
В соответствии с последовательностью, определенной заданием на лабораторную работу, были выполнены следующие действия:
- [X] 1. Для успешного выполнения задания создан новый пустой репозиторий lab13 с лицензией MIT.
- [X] 2. Выполнена следующая последовательность команд:

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=woz91
```

```ShellSession
$ git clone https://github.com/${GITHUB_USERNAME}/lab12 lab13
$ cd lab13
$ git remote remove origin
$ git remote add origin git@github.com:${GITHUB_USERNAME}/lab13
```

```ShellSession
$ cat > Dockerfile <<EOF
FROM ubuntu:16.04
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

RUN apt update
RUN apt install -yy gcc g++ cmake 
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

COPY . print/
WORKDIR print
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
RUN cmake --build _build
RUN cmake --build _build --target install
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

ENV LOG_PATH /home/logs/log.txt
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

VOLUME /home/logs
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

WORKDIR _install/bin
EOF
```

```ShellSession
$ cat >> Dockerfile <<EOF

CMD ./demo
EOF
```

```ShellSession
$ sudo usermod -a -G docker $USER
$ docker build -t logger .
```

```ShellSession
$ docker images
```

```ShellSession
$ mkdir logs
$ docker run -it -v "$(pwd)/logs/:/home/logs/" logger
text1
text2
text3
<C-D>
```

```ShellSession
$ docker inspect logger
```

```ShellSession
$ cat logs/log.txt
```

```ShellSession
$ vim README.md
:s/lab12/lab13/g<CR>
:wq
```

```ShellSession
$ vim .travis.yml
/lang<CR>o
services:
  - docker<ESC>
jVGddo
script:
  - docker build -t logger .<ESC>
```

```ShellSession
$ git add Dockerfile
$ git add .travis.yml
$ git commit -m"adding Dockerfile"
$ git push origin master
```

```ShellSession
$ travis login --auto
$ travis enable
```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=13
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```


- [X] 3. Проведено ознакомление по приведенным ссылкам со следующими материалами по [Instructions](https://docs.docker.com/engine/reference/builder/), [Book](https://www.dockerbook.com).

- [X] 4. Составлен отчет о работе в формате MD, ссылка отправлена в **slack**.

	
>## Выводы:

>В ходе проделанной работы проведено ознакомление с работой ситсемы автоматизации развертывания и управления приложениями **Docker**, создан контейнер, на котором автоматизированно развенуто приложение, получен вывод приложения, который записан в файл **log.txt**.

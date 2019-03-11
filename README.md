## Laboratory work I

Данная лабораторная работа посвещена изучению утилит для разработки проектов

## Tasks

- [x] 1. Ознакомиться со ссылками учебного материала
- [x] 2. Выполнить инструкцию учебного материала
- [x] 3. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial
Добавляем переменные окружения GITHUB_USERNAME и GIST_TOKEN, связываем команду edit с текстовым редактором.
```bash
# Присваиваем переменной GITHUB_USERNAME свое имя пользователя на Github  
$ export GITHUB_USERNAME=Ais105
# Вводим для переменной GIST_TOKEN созданный token для работы с Gist
$ export GIST_TOKEN=****************************************
# Cвязываем команду edit с вызовом текстового редактора vim
$ alias edit=vim
```
Создание рабочей директории workspace для дальнейшей работы.
```ShellSession
# Cоздаем директорию со вложенной папкой workspace
$ mkdir -p ${GITHUB_USERNAME}/workspace
# Переходим к созданной директории
$ cd ${GITHUB_USERNAME}/workspace
# Выводим полный путь до нащей директории
$ pwd
/home/kristina/Ais105/workspace
# Переходим к предидущей директории
$ cd ..
# Выводим полный путь до текущей директории
$ pwd
/home/kristina/Ais105
```
Создаем подкаталоги в директории workspace.
```ShellSession
# Создаем дочерние директории в каталоге workspace
$ mkdir -p workspace/tasks/
$ mkdir -p workspace/projects/
$ mkdir -p workspace/reports/
# Переходим к каталогу workspace
$ cd workspace
```
Устанавливаем nodejs в рабочую директорию для дальнейшей работы.
```ShellSession
# Ubuntu
# Скачиваем архив с последней версией nodejs
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
# Распаковываем архив
$ tar -xf node-v6.11.5-linux-x64.tar.xz
# Удаляем архив
$ rm -rf node-v6.11.5-linux-x64.tar.xz
# Переименовываем каталог
$ mv node-v6.11.5-linux-x64 node
```
Просматриваем содержимое каталога node/bin, добавляем директорию с nodejs в переменную PATH для работы в терминале.
```ShellSession
# Просмотр содержимого каталога node/bin
$ ls node/bin
node npm
# Выводим список директорий, где терминал ищет исполняемые файлы
$ echo ${PATH}
/home/kristina/bin:/home/kristina/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
# Добавление к переменной PATH пути до бинарных файлов nodejs
$ export PATH=${PATH}:`pwd`/node/bin
# Снова выводим список
$ echo ${PATH}
/home/kristina/bin:/home/kristina/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/kristina/Ais105/workspace/node/bin
# Создание каталога scripts
$ mkdir scripts
# Создание файла activate в этом каталоге
$ cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
# Исполнение содержимого файла как набора команд
$ source scripts/activate
```
Устанавливаем gistup для создания gist из терминала.
```ShellSession
# Устанавливаем gistup при помощи npm
$ npm install -g gistup
/home/kristina/Ais105/workspace/node/bin/gistup -> /home/kristina/Ais105/workspace/node/lib/node_modules/gistup/bin/gistup
/home/kristina/Ais105/workspace/node/bin/gistup-open -> /home/kristina/Ais105/workspace/node/lib/node_modules/gistup/bin/gistup-open
/home/kristina/Ais105/workspace/node/bin/gistup-rename -> /home/kristina/Ais105/workspace/node/lib/node_modules/gistup/bin/gistup-rename
/home/kristina/Ais105/workspace/node/lib
└─┬ gistup@0.1.3 
├─┬ optimist@0.3.7 
│ └── wordwrap@0.0.3 
└── queue-async@1.2.1 
# выводим список файлов директории node/bin (проверяем становку)
$ ls node/bin
gistup gistup-open gistup-rename node npm
```
Создаем файл .gistup.json, где будет находиться gist token.
```ShellSession
# Создание файла .gistup.json, где находится gist token
$ cat > ~/.gistup.json <<EOF
{
  "token": "${GIST_TOKEN}"
}
EOF
```

## Report

```ShellSession
# Добавление переменной с номером лабораторной работы
$ export LAB_NUMBER=01
# Клонирование репозитория в директорию tasks/lab01
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
# Создание директории
$ mkdir reports/lab${LAB_NUMBER}
# Копирование файла в созданную директорию
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
# Переход в каталог reports/lab01
$ cd reports/lab${LAB_NUMBER}
# Редактирование файла 
$ edit REPORT.md
# Создание gist 
$ gistup -m "lab${LAB_NUMBER}" # enter: yes↵
```

## Links

### Unix commands

- [ar](https://en.wikipedia.org/wiki/Ar_(Unix))
- [cat](https://en.wikipedia.org/wiki/Cat_(Unix))
- [cd](https://en.wikipedia.org/wiki/Cd_(command))
- [cp](https://en.wikipedia.org/wiki/Cp_(Unix))
- [cut](https://en.wikipedia.org/wiki/Cut_(Unix))
- [echo](https://en.wikipedia.org/wiki/Echo_(command))
- [env](https://en.wikipedia.org/wiki/Env_(shell))
- [ex](https://en.wikipedia.org/wiki/Ex_(editor))
- [file](https://en.wikipedia.org/wiki/File_(command))
- [find](https://en.wikipedia.org/wiki/Find)
- [ls](https://en.wikipedia.org/wiki/Ls)
- [man](https://en.wikipedia.org/wiki/Man_page)
- [mkdir](https://en.wikipedia.org/wiki/Mkdir)
- [mv](https://en.wikipedia.org/wiki/Mv)
- [nm](https://en.wikipedia.org/wiki/Nm_(Unix))
- [ps](https://en.wikipedia.org/wiki/Ps_(Unix))
- [pwd](https://en.wikipedia.org/wiki/Pwd)
- [rm](https://en.wikipedia.org/wiki/Rm_(Unix))
- [sed](https://en.wikipedia.org/wiki/Sed)
- [touch](https://en.wikipedia.org/wiki/Touch_(Unix))

### Package Managers

- [apt](http://help.ubuntu.ru/wiki/apt) | [dnf](https://en.wikipedia.org/wiki/DNF_(software)) | [yum](https://fedoraproject.org/wiki/Yum/ru)
- [brew](https://brew.sh) | [linuxbrew](http://linuxbrew.sh)
- [npm](https://docs.npmjs.com)

### Software

- [curl](https://www.gitbook.com/book/bagder/everything-curl/details)
- [wget](https://www.gnu.org/software/wget/manual/wget.pdf)
- [clang](https://clang.llvm.org)
- [g++](https://gcc.gnu.org/onlinedocs/gcc-4.0.2/gcc/G_002b_002b-and-GCC.html)
- [make](https://en.wikipedia.org/wiki/Make_(software))
- [open](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/open.1.html)
- [openssl](https://www.openssl.org)
- [nano](https://www.nano-editor.org)
- [tree](https://linux.die.net/man/1/tree)
- [vim](http://www.vim.org)

### Homework

1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
```ShellSession
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz #скачиваем архив
```
2. Разархивируйте скачанный файл в директорию ~/boost_1_69_0
```ShellSession
$ tar -xf boost_1_69_0.tar.gz # распаковываем архив
$ rm -rf boost_1_69_0.tar.gz # удаляем архив
$ cd boost_1_69_0 # переходим в каталог с *boost*
```
3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
```ShellSession
$ ls -f . | wc -l
20
```
4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
```ShellSession
$ find . -type f | wc -l
61192
```
5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
```ShellSession
$ find . -type f -name '*.h' | wc -l
296
$ find . -type f -name '*.cpp' | wc -l
13774
$ find . -type f '!' -name '*.cpp' -a '!' -name '*.h' | wc -l
47121
```
6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.
```ShellSession
$ find . -type f -name 'any.hpp'
./boost/type_erasure/any.hpp
./boost/proto/detail/any.hpp
./boost/fusion/algorithm/query/detail/any.hpp
./boost/fusion/algorithm/query/any.hpp
./boost/fusion/include/any.hpp
./boost/xpressive/detail/utility/any.hpp
./boost/hana/fwd/any.hpp
./boost/hana/any.hpp
./boost/spirit/home/support/algorithm/any.hpp
./boost/any.hpp
```
7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
```ShellSession
$ grep -lr 'boost::asio' 
boost/asio/read_at.hpp
...
libs/coroutine/doc/motivation.qbk
```
8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
```ShellSession
# prefix указывает в какой папке будут скомпилированы библиотеки и include файлы
$ ./bootstrap.sh --prefix=boost_output 
$ ./b2 install
```
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
```ShellSession
$ cd ..
$ mv boost_1_69_0/boost_output boost-libs
```
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
```ShellSession
$ du -h
```
11. Найдите топ10 самых "тяжёлых".
```ShellSession
$ find .  -type f -exec du -sh {} 2>/dev/null + | sort -rh | head -n 10
```
Copyright (c) 2015-2019 The ISC Authors



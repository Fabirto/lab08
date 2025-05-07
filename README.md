$ export GITHUB_USERNAME=Fabirto
$ export GITHUB_TOKEN=токен

создает переменные

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
$ source scripts/activate
изменяет директорию, запускает файл

$ \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
скачивает rvm

$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
Добавляет команду для загрузки RVM в файл

$ . scripts/activate
Запускает скрипт

$ rvm autolibs disable
Отключает автоматическую установку системных библиотек

$ rvm install ruby-2.4.2
$ rvm use 2.4.2 --default
Устанавливает Ruby 2.4.2

$ gem install travis
Устанавливает инструмент командной строки travis

$ git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab04
$ cd projects/lab04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab04
копирует репозиторий, добавляет оригин

$ cat > .travis.yml <<EOF
language: cpp
EOF
создает файл

$ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
создает файл

$ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
создает файл

$ travis login --github-token ${GITHUB_TOKEN}
авторизация в тревис

$ travis lint
Проверяет корректность файла .travis.yml

$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
вставляет текст в readme

$ git add .travis.yml
$ git add README.md
$ git commit -m"added CI"
$ git push origin master
сохраняет файлы в репозиторий

$ travis lint
 Проверяет конфигурацию .travis.yml
$ travis accounts
 Выводит информацию о репозиториях
$ travis sync
 Синхронизирует и обновляет данные 
$ travis repos
 Выводит информацию о репозиториях
$ travis enable
 Включает CI/CD для репозитория
$ travis whatsup
$ travis branches
$ travis history
$ travis show
 Показывает статус сборок




 $ popd
$ export LAB_NUMBER=04
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md

$ export GITHUB_USERNAME=Fabirto
$ export GITHUB_EMAIL=sweatytryhardyes@gmail.com
$ export GITHUB_TOKEN=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
$ alias edit=vim
то же, что и в 1 лр


$ cd ${GITHUB_USERNAME}/workspace
$ source scripts/activate

cоздает директорию workspace, активирует скрипт activate
$ mkdir ~/.config
$ cat > ~/.config/hub <<EOF
github.com:
user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF
$ git config --global hub.protocol https
 создает .config, создает файл hub в .config и записывает в него конфигурацию для hub, настраивает git на использование протокола HTTPS для  hub

$ mkdir projects/lab02 && cd projects/lab02
$ git init
$ git config --global user.name ${GITHUB_USERNAME}
$ git config --global user.email ${GITHUB_EMAIL}
# check your git global settings
$ git config -e --global
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git
$ git pull origin main(MAIN вместо MASTER, MASTER устарел)
$ touch README.md
$ git status
$ git add README.md
$ git commit -m"added README.md"
$ git push origin main
настраивает репозиторий, добавляет файл, загружает в репозиторий

*build*/
*install*/
*.swp
.idea/
-указывает то, что нужно игнорировать-





$ git pull origin master
$ git log
обновляет master, показывает историю изменений




$ mkdir sources
$ mkdir include
$ mkdir examples
$ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
создает директории, создает файл и записывает в него команды


$ cat > include/print.hpp <<EOF
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF






$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
-создает файл exapmle1.cpp в examples, записывает в него код-



$ cat > examples/example2.cpp <<EOF
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
создает файл exapmle2.cpp в examples, записывает в него код





$ edit README.md
 открывает файл README





  
$ git status
$ git add .
$ git commit -m"added sources"
$ git push origin master
показывает статус, добавляет изменения, сохраняет, загружает в репозиторий







$ cd ~/workspace/
$ export LAB_NUMBER=02
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
клонирует репозиторий, клонирует и переносит REPORT, открывает REPORT




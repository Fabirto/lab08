$ export GITHUB_USERNAME=Fabirto
$ alias gsed=sed # for *-nix system

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
$ source scripts/activate
изменяет дирректорию, активирует скрипт

$ git clone https://github.com/${GITHUB_USERNAME}/lab04 projects/lab05
$ cd projects/lab05
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab05
клонирует репозиторий, добавляет оригин

$ mkdir third-party
$ git submodule add https://github.com/google/googletest third-party/gtest
$ cd third-party/gtest && git checkout release-1.8.1 && cd ../..
$ git add third-party/gtest
$ git commit -m"added gtest framework"
создает директорию, добавляет в нее гуглтест, переключает  версию, добавляет файл в гит

$ gsed -i '/option(BUILD_EXAMPLES "Build examples" OFF)/a\
option(BUILD_TESTS "Build tests" OFF)
' CMakeLists.txt
добавляет в cmake новую строчку


$ cat >> CMakeLists.txt <<EOF

if(BUILD_TESTS)
  enable_testing()
  add_subdirectory(third-party/gtest)
  file(GLOB \${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
  add_executable(check \${\${PROJECT_NAME}_TEST_SOURCES})
  target_link_libraries(check \${PROJECT_NAME} gtest_main)
  add_test(NAME check COMMAND check)
endif()
EOF
создает файл

$ mkdir tests
$ cat > tests/test1.cpp <<EOF
#include <print.hpp>

#include <gtest/gtest.h>

TEST(Print, InFileStream)
{
  std::string filepath = "file.txt";
  std::string text = "hello";
  std::ofstream out{filepath};

  print(text, out);
  out.close();

  std::string result;
  std::ifstream in{filepath};
  in >> result;

  EXPECT_EQ(result, text);
}
EOF
создает директорию, создает файл

$ cmake -H. -B_build -DBUILD_TESTS=ON
 Генерирует файлы сборки с включёнными тестами
$ cmake --build _build
 Компилирует проект и тесты
$ cmake --build _build --target test
Выполняет тесты и выводит результаты

$ _build/check
Запускает исполняемый файл

$ cmake --build _build --target test -- ARGS=--verbose
Запускает исполняемый файл с аргументами

$ gsed -i 's/lab04/lab05/g' README.md
Заменяет все вхождения lab04 на lab05 в README.md


$ gsed -i 's/\(DCMAKE_INSTALL_PREFIX=_install\)/\1 -DBUILD_TESTS=ON/' .travis.yml
В файле .travis.yml добавляет флаг -DBUILD_TESTS=ON к строке с DCMAKE_INSTALL_PREFIX

$ gsed -i '/cmake --build _build --target install/a\
Добавляет запуск тестов с --verbose после команды install в .travis.yml

- cmake --build _build --target test -- ARGS=--verbose
- запускает файл
' .travis.yml

$ travis lint
Проверяет синтаксис .travis.yml на ошибки

$ git add .travis.yml
$ git add tests
$ git add -p
$ git commit -m"added tests"
$ git push origin master
добавляет файлы и делает пуш

$ travis login --auto
$ travis enable
авторизируется в тевисе, активирирует сборку

$ mkdir artifacts
$ sleep 20s && gnome-screenshot --file artifacts/screenshot.png
# for macOS: $ screencapture -T 20 artifacts/screenshot.png
# open https://github.com/${GITHUB_USERNAME}/lab05
создает папку, делает скриншот

Report

$ popd
$ export LAB_NUMBER=05
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md

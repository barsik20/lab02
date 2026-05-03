# Lab02 Project


### Оглавление данных

```bash
export GITHUB_USERNAME=barsik20
export GITHUB_EMAIL=bars.070620077777@gmail.com
export GITHUB_TOKEN=<token>
alias edit=nano

cd ${GITHUB_USERNAME}/workspace
source scripts/activate
```

#### Настройка доступа к GitHub

```bash
mkdir ~/.config
cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF

git config --global hub.protocol https
```

---

#### Создание папки c lab02

```bash
mkdir -p projects/lab02
cd projects/lab02
git init
```

#### Настройка Git

```bash
git config --global user.name ${GITHUB_USERNAME}
git config --global user.email ${GITHUB_EMAIL}
git config -e --global
```

---

#### Подключение удалённого репозитория с помощью команды git

```bash
git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git
git pull origin master
```

---

#### Добавляем README.md

```bash
touch README.md
git add README.md
git commit -m "added README.md"
git push origin master
```

---

#### Создание`.gitignore`

Содержимое файла:

```
*build*/
*install*/
*.swp
.idea/
```

```bash
git pull origin master
git log
```

---

#### Создание трёх папок

```bash
mkdir sources include examples
```

---

#### Создаем файл с помощью команды cat и с расширениями файлов .cpp .hpp

**sources/print.cpp**

```cpp
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
```

**include/print.hpp**

```cpp
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
```

**examples/example1.cpp**

```cpp
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
```

**examples/example2.cpp**

```cpp
#include <print.hpp>
#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
```

---

#### Финальный коммит

```bash
git add .
git commit -m "added sources"
git push origin master
```


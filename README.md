# Проект по курсу Компьютерные сети

Этот проект представляет из себя пользовательский интернет-сервис для проведения конференции. 
Приложение содержит данные о пользователе, докладе и конференции. Также были реализованы следующие REST API:
- Создание нового пользователя
- Поиск пользователя по логину
- Поиск пользователя по маске имя и фамилии
- Создание доклада
- Получение списка всех докладов
- Добавление доклада в конференцию
- Получение списка докладов в конференции
Более полное описание есть в файле [index.yaml](main/server/index.yaml)
Также было реализовано распределение данных по нескольким серверам (Sharding) с применением программного обеспечения ProxySQL. Выполнение вспомогательного программного обеспечения выполняется с помощью технологии контейнеризации Docker.

Более детальное опаисание проекта со схемами взаимодействий находится в директории [template](app_structure/template) 

## Запуск
1. Запуск docker производится из папки [docker](main/server/docker) командой:

```docker-compose up --build```

2. Build осуществляется с помощью CMake.

3. Приложение запускается командой: 

```sudo ./build/hl_mai_lab_01 --host=localhost --port=3306 --login=stud --password=stud --database=stud```

4. Заполнение базы данных статей осуществляется в директории [fill_articles](main/server/fill_articles), а информаци о докладчиках в [fill_persons](main/server/fill_persons), build также осуществляется с помощью CMake.


## Зависимости
Необходимо установить следующие зависимости:

```
sudo apt update
sudo apt upgrade
sudo apt install -y build-essential autoconf libtool pkg-config gcc g++ cmake git libssl-dev zlib1g-dev librdkafka-dev mysql-server mysql-client libmysqlclient-dev libboost-all-dev openjdk-8-jdk openjdk-8-jre default-jdk libgtest-dev
cd /usr/src/gtest/
sudo cmake -DBUILD_SHARED_LIBS=ON
sudo make
sudo cp lib/*.so /usr/lib
cd
git clone -b master https://github.com/pocoproject/poco.git
cd poco
mkdir cmake-build
cd cmake-build
cmake ..
cmake --build . --config Release
sudo cmake --build . --target install
cd
```


  

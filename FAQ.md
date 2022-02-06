После курса такое надо уметь:
-------------------------

### Запустить Python
Создаем в Visual Studio Code файл с типом Dockerfile и пишем в нем, что именно хотим поднять и с какими преднастройками.
После этого мы должны сделать 
docker build -t test:pandas .
точка - это значит, что в этой директории с текущим файлом он создаст все нужные файлы именно тут и сам файл отсюда же возьмет
-t test - тут это тэг, имя image, а pandas - это версия

после построения image мы можем запустить

docker run -it test:pandas

### Запустить Airflow

### Запустить PostgreSQL в сети с Airflow

### Собрать контейнер для запуска в docker с нуля
Как составить yaml файл для запуска docker compose, который одновременно поднимает pgadmin и postgres

### С помощью Terraform залить данные в Google Clowd Storage

### С помощью Transfer Service залить данные из Amazon Web Services в Google Clowd Storage



### Как из питона постучаться в постгрес
  from sqlalchemy import create_engine
  engine = create_engine(f'postgresql://{user}:{password}@{host}:{port}/{db}')
      engine.connect()

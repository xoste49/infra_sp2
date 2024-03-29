# API YaMDb
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).<br/>
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.<br/>
В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.<br/>
Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.<br/>
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

### Шаблон наполнения env-файла
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

### Quick Start from Docker
Описание команд для запуска приложения в Docker контейнерах
```
git clone https://github.com/xoste49/infra_sp2
cd infra_sp2
cd infra
docker-compose up -d
# Создание миграций
docker-compose exec web python manage.py migrate
# Сбор статики
docker-compose exec web python manage.py collectstatic
# Заполняем начальными данными
docker-compose exec web python manage.py loaddata fixtures.json
# Создаём администратора
docker-compose exec web python manage.py createsuperuser
# Перезапускаем контейнеры
docker-compose restart
```

### Команды
`docker-compose exec web python manage.py dumpdata > dumpdata.json` - создание дампа<br/>
`docker cp dumpdata.json infra_web_1:/app; docker-compose exec web python manage.py loaddata dumpdata.json` - загрузка из дампа

### Contact me
GitHub - [@github/xoste49](https://github.com/xoste49)<br/>
Telegram - https://t.me/xoste49
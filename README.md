# «FOODGRAM».
 ### Описание

 ### Технологии
 Python 3.8, DRF 3.12, JWT + Djoser
 ### Запуск проекта в dev-режиме
 - Склонируйте репозиторий.
 - Установите и активируйте виртуальное окружение:
 ```bash
 py -3.8 -m venv venv
 venv/Scripts/activate
 python -m pip install --upgrade pip
 ```
 - Устиновите зависимости из файла requirements.txt
 ```bash
 pip install -r requirements.txt
 ```
 - Выполните миграции:
 ```bash
 python manage.py migrate
 ```
 Создайте суперпользователя:
 ```bash
 python manage.py createsuperuser
 ```
 Запустите проект:
 ```bash
 python manage.py runserver
 ```
 ### Примеры работы с API для всех пользователей
 Для неавторизованных пользователей работа с API доступна в режиме чтения.
 ```bash
 GET api/recipes/ - получить список всех рецептов.
 При указании параметров limit и offset выдача должна работать с пагинацией
 GET api/recipes/{id}/ - получение рецепта по id

 GET api/v1/tags/ - получение списка тегов
 GET api/v1/tags/{id}/ - получение информации о теге  по id

 GET api/ingredients/ - получение всех ингредиентов
 GET api/ingredients/ - Получение конкетного ингредиента
 ```
 ### Примеры работы с API для авторизованных пользователей
 Для создания публикации используем:
 ```bash
 POST /api/recipe/
 ```
 в body
{
  "ingredients": [
    {
      "id": 1123,
      "amount": 10
    }
  ],
  "tags": [
    1,
    2
  ],
  "image": "картинка",
  "name": "string",
  "text": "string",
  "cooking_time": 1
}


 ```bash
 GET api/users/subscriptions/ - Возвращает пользователей, на которых подписан текущий пользователь. В выдачу добавляются рецепты.
 ```
 - Авторизованные пользователи могут создавать рецепты,
добавлять их в избранное.
 - Пользователи могут изменять(удалять) контент, автором которого они являются.


 ```
 Доступ авторизованным пользователем доступен по JWT-токену (Joser)
 Используется для авторизации по емейлу и паролю, чтобы далее использовать токен при запросах.
 ```bash
 POST api/auth/token/login/
 ```
 Передав в body данные пользователя (например в postman):
 ```bash
{
  "password": "string",
  "email": "string"
}
 ```
 Полученный токен добавляем в headers (postman), после чего буду доступны все функции проекта:
 ```bash
 Authorization: Token {your_token}
 ```


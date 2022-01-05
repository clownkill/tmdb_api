# tmdb_api
Набор утилит для работы с базой фильмов [The Movie Data Base](https://www.themoviedb.org/).
## Работа с API
### tmdb_helpers.py
Модуль для проверки api-ключа и выполнения запросов к api [TMDB](https://www.themoviedb.org/). Проверяет его. Выполняет запросы к api, и возвращает результат в виде словаря.

### hello_api_TMDB.py
Модуль запрашивает у пользователя api-ключ для проверки доступа к api TMDB. В случае не удачной попытки подключения выводит в консоль сообщение о некорректности ключа `Invalid api key` и завершает работу. Если проверка ключа успешна, то выполняется пробное подключение и в консоль выводится бюджет фильма из базы данных под номером 215.

Для проверки api-ключа и выполнения запроса используются модуль `tmdb_helpers`.

### make_own_db.py
Модуль запрашивает у пользователя api-ключ и проверяет его. В случае не удачной попытки подключения выводит в консоль сообщение о некорректности ключа `Invalid api key` и завершает работу. Если проверка ключа успешна в консоль выводится сообщение: `please, wait, this operation may take smth like 15-20 minutes` и выполняется создание локальной базы данных по первым 1000 фильмам. Во время создания базы данных в консоль выводятся строки с процентом выполнения в реальном времени. База данных сохраняется в файле `MyFilmDB.json`.

Для проверки api-ключа и выполнения запроса данных о фильмах для создания базы данных используется модуль `tmdb_helpers`.

## Работа с локальной базой данных

### own_db_helpers.py
Модуль проверяет наличие базы данных по полученному пути. При наличии файла базы данных возвращает данные о фильмах в виде словаря.

### search_in_db.py
Модуль запрашивает у пользователя путь до файла с локальной базой данных. Проверяет наличие файла по указанному пути и осуществляет поиск ключевого слова, введенного пользователем, по названию фильмов в базе данных. Выводит отсортированный список найденных фильмов.

Для проверки пути к файлу базы данных и доступа к базе используется модуль `own_db_helpers`.

### find_similar.py
Модуль запрашивает у пользователя путь до файла с локальной базой данных. Проверяет наличие файла по указанному пути, и при удачном подключении к локальной базе данных запрашивает фильм для поиска и пытается найти его. Если находит, то выводит отсортированный список найденных фильмов. Подбор рекомендованных фильмов осуществляется поиском совпадений по бюджету, жанру, оригинальному языку и принадлежности к одной коллекции. Самым важным параметром является коллекция, затем жанр, потом язык и в последнюю очередь бюджет. В случае неудачного подключения к базе данных или невозможности найти фильм в ней работа скрипта завершается.
 
Для проверки пути к файлу базы данных и доступа к базе используется модуль `own_db_helpers`.

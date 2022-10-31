# yandex-music-downloader

## Содержание
1. [О программе](#О-программе)
2. [Установка](#Установка)
3. [Получение данных для авторизации](#Получение-данных-для-авторизации)
4. [Использование](#Использование)
5. [Спасибо](#Спасибо)
6. [Дисклеймер](#Дисклеймер)


## О программе
Загрузчик, созданный вследствие наличия *фатального недостатка* в проекте [yandex-music-download](https://github.com/kaimi-io/yandex-music-download).

### Возможности
- Возможность загрузки:
    - Всех треков исполнителя
    - Всех треков из альбома
    - Всех треков их плейлиста
    - Отдельного трека
- Загрузка всех метаданных трека/альбома:
    - Номер трека
    - Номер диска
    - Название трека
    - Исполнитель
    - Дополнительные исполнители
    - Год выпуска альбома
    - Обложка альбома
    - Название альбома
    - Текст песни (при использовании флага `--add-lyrics`)
- Поддержка паттерна для пути сохранения музыки
- Загрузка без задержек между запросами

## Установка
```
git clone https://gitlab.com/llistochek/yandex-music-download
cd yandex-music-download
pip install -r requirements.txt
python3 main.py
```

## Получение данных для авторизации
Войдите в свой Яндекс аккаунт, затем проделайте следующие шаги:

### Для Google Chrome/Chromium
1. Перейдите на сайт Яндекс Музыки (https://music.yandex.ru) 
2. Нажмите F12
3. Выберите вкладку Application
4. Выберите пункт Cookies->https://music.yandex.ru
5. Скопируйте значение куки (кликните на значение куки 2 раза -> Ctrl+C):
    - Куки `spravka` - это аргумент `--spravka`
    - Куки `Session_id` - это аргумент `--sesion-id`


### Для Firefox
1. Перейдите на сайт Яндекс Музыки (https://music.yandex.ru) 
2. Нажмите F12
3. Выберите вкладку Storage
4. Выберите пункт Куки->https://music.yandex.ru
5. Скопируйте значение куки (кликните на значение куки 2 раза -> Ctrl+C):
    - Куки `spravka` - это аргумент `--spravka`
    - Куки `Session_id` - это аргумент `--sesion-id`

## Использование

```
usage: main.py [-h] [--hq] [--skip-existing] [--cover-resolution <Разрешение обложки>] [--add-lyrics] [--delay <Задержка>] [--log-level {CRITICAL,FATAL,ERROR,WARN,WARNING,INFO,DEBUG,NOTSET,VERBOSE}]
               (--artist-id <ID исполнителя> | --album-id <ID альбома> | --track-id <ID трека> | --playlist-id <владелец плейлиста>/<тип плейлиста> | -u URL) [--dir <Папка>] [--path-pattern <Паттерн>]
               --session-id <ID сессии> --spravka <Справка> --user-agent <User-Agent>

Загрузчик музыки с сервиса Яндекс.Музыка

optional arguments:
  -h, --help            show this help message and exit

Общие параметры:
  --hq                  Загружать треки в высоком качестве (по умолчанию: False)
  --skip-existing       Пропускать уже загруженные треки (по умолчанию: False)
  --cover-resolution <Разрешение обложки>
                        (по умолчанию: 400)
  --add-lyrics          Загружать тексты песен (по умолчанию: False)
  --delay <Задержка>    Задержка между запросами, в секундах (по умолчанию: 0)
  --log-level {CRITICAL,FATAL,ERROR,WARN,WARNING,INFO,DEBUG,NOTSET,VERBOSE}

ID:
  --artist-id <ID исполнителя>
  --album-id <ID альбома>
  --track-id <ID трека>
  --playlist-id <владелец плейлиста>/<тип плейлиста>
  -u URL, --url URL     URL исполнителя/альбома/трека/плейлиста

Указание пути:
  --dir <Папка>         Папка для загрузки музыки (по умолчанию: .)
  --path-pattern <Паттерн>
                        Поддерживает следующие заполнители: #number, #artist, #title, #album, #year (по умолчанию: #artist/#album/#number - #title)

Авторизация:
  --session-id <ID сессии>
  --spravka <Справка>
  --user-agent <User-Agent>
```

## Спасибо
Разработчикам проекта [yandex-music-download](https://github.com/kaimi-io/yandex-music-download). Оттуда был взят [код хэширования](https://github.com/kaimi-io/yandex-music-download/blob/808443cb32be82e1f54b2f708884cb7c941b4371/src/ya.pl#L720).

## Дисклеймер
Данный проект является независимой разработкой и никак не связан с компанией Яндекс.
# Перевод текста

[!INCLUDE [speechkit-v1-disclaimer.md](../../../_includes/speechkit-v1-disclaimer.md)]

Переводит заданный текст на указанный язык.

## Запрос {#request}

```
POST https://translate.api.cloud.yandex.net/translate/v1/translate
```

### Параметры в теле запроса

Для всех параметров обязательно используйте URL-кодирование. Максимальный размер тела POST-запроса 30 КБ.


Параметр | Описание
----- | -----
`text` | Обязательный параметр.<br/>Текст, который необходимо перевести, в кодировке UTF-8.<br/>В запросе можно использовать несколько параметров `text`.
`source` | Язык, на котором написан исходный текст.<br/>Задается в виде двухбуквенного кода языка в соответствии с [ISO-639-1](https://en.wikipedia.org/wiki/ISO_639-1) (например `ru`). Если параметр не задан, сервис пытается определить исходный язык автоматически.
`target` | Обязательный параметр.<br/>Направление перевода.<br/>Задается в виде двухбуквенного кода языка в соответствии с [ISO-639-1](https://en.wikipedia.org/wiki/ISO_639-1) (например `ru`).
`format` | Формат текста.<br/>Возможные значения:<br/><ul><li>`plain` — текст без разметки (значение по умолчанию)</li><li>`html` — текст в формате HTML.</li></ul>
`folderId` | Обязательный параметр.<br/>Идентификатор вашего каталога.<br/>Подробнее о том, как узнать идентификатор каталога читайте в разделе [Авторизация в API](../../concepts/auth.md).



## Ответ {#response}

Ответ возвращается в формате JSON.

```json
{
    "translations": [
        {"text": <перевод текста>},
        ...
    ]
}
```


## Примеры {#examples}

### Пример запроса

```httpget
export FOLDER_ID=<folder id>
export TOKEN=<IAM-token>
curl -X POST \
     -H "Authorization: Bearer ${TOKEN}" \
     -d "folderId=${FOLDER_ID}&target=en" \
     --data-urlencode "text=привет мир" \
     --data-urlencode "text=доброе утро" \
     "https://translate.api.cloud.yandex.net/translate/v1/translate"
```

### Пример ответа

Ответ возвращается в формате JSON.

```json
{
    "translations": [
        {
            "text": "Hello world"
        },
        {
            "text": "good morning"
        }
    ]
}
```


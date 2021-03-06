# Вопросы и ответы про [!KEYREF objstorage-full-name]

#### Что такое [!KEYREF objstorage-full-name]? {#qa-what-is}

[!KEYREF objstorage-full-name] — это универсальное масштабируемое решение для хранения данных. Оно подходит как для высоконагруженных сервисов, которым требуется надежный и быстрый доступ к данным, так и для проектов с невысокими требованиями к инфраструктуре хранения.

#### Что я могу делать с [!KEYREF objstorage-full-name]? {#qa-usecases}

С [!KEYREF objstorage-name] вы можете:
- Разместить в [!KEYREF objstorage-name] файлы своего проекта (сайта или серверного приложения) для публичного или закрытого доступа. Файлы могут быть любого формата.
- Хранить архивные данные большого объема (до 5TB на один файл), которые будут доступны только тем, кому вы разрешите.
- Обеспечить совместную работу с данными внутри распределенной организации.
- Обеспечить доступ к своим данным из любого места Земли, где есть интернет.

#### Как начать пользоваться [!KEYREF objstorage-full-name]? {#qa-quickstart}

Чтобы начать работать с [!KEYREF objstorage-name]:
1. Зарегистрируйтесь в Яндекс.Облаке.
1. Создайте каталог.
    На этом шаге уже можно пользоваться [!KEYREF objstorage-name] с помощью консоли управления Яндекс.Облака. Можно создавать и удалять бакеты, загружать объекты в бакеты и скачивать их оттуда.
1. Получите статические ключи, чтобы использовать HTTP API [!KEYREF objstorage-name] или готовые SDK и приложения.

Более подробные инструкции вы найдете в разделах [[!TITLE]](quickstart.md) и [[!TITLE]](s3/index.md).

#### Какие форматы данных я могу хранить? {#qa-data-types}

Вы можете хранить данные в любом формате. [!KEYREF objstorage-full-name] сохраняет данные в изначальном виде, никаким образом их не преобразовывая.

#### Как мне оставить отзыв на [!KEYREF objstorage-full-name]? {#qa-feedback}

Воспользуйтесь формой обратной связи на странице поддержки в консоли управления.

#### Как обратиться в службу технической поддержки? {qa-support-channels}

Вы можете обратиться в службу технической поддержки в разделе [Поддержка](https://console.cloud.yandex.ru/support) 
в консоли управления.

#### Сколько я могу хранить данных? {#qa-storage-volume}

Ознакомьтесь с разделом [[!TITLE]](concepts/limits.md).

#### Как удалить несколько объектов за один раз? {#qa-delete-multiple-objects}

Вы можете удалить несколько объектов через консоль управления Яндекс.Облака или через API с помощью метода [deleteMultipleObjects](s3/api-ref/object/deletemultipleobjects.md).

#### Что Яндекс делает с данными, которые я храню в [!KEYREF objstorage-full-name]? {#qa-data-use-by-yandex}

Данные сохраняются в том виде, в котором их передал пользователь.

#### Использует ли Яндекс [!KEYREF objstorage-name] для размещения своих данных? {#qa-usage-by-yandex}

Да. [!KEYREF objstorage-name] используется в инфраструктуре Яндекса. Несколько сервисов Яндекса держат в хранилище статические данные для своих сайтов.

#### Какую модель консистентности данных использует [!KEYREF objstorage-full-name]? {#qa-consistency}

Для перезаписываемых (PUT) или удаляемых (DELETE) объектов используется консистентность в конечном счете (eventual consistency).

#### Какие возможности AWS S3 поддерживаются в [!KEYREF objstorage-full-name]? {#qa-s3-support}

В [!KEYREF objstorage-name] поддерживаются:

- Авторизация статическими токенами.
- Некоторые методы HTTP API. Полный список поддерживаемых методов смотрите в [Справочнике API](s3/api-ref/index.md).


#### Где хранятся мои данные? {#qa-where}

Данные хранятся в нескольких географически распределенных датацентрах на территории России.

#### Как защищены мои данные в [!KEYREF objstorage-full-name]? {#qa-data-security}

Физические носители расположены в датацентрах Яндекса, которые являются режимными объектами.

Данные хранятся в зашифрованном виде и никто из тех, кто имеет доступ к физическому носителю не сможет прочитать данные.

По умолчанию доступ к хранилищу осуществляется по протоколу HTTPS.

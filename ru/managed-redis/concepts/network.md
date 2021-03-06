# Сеть и кластеры [!KEYREF mrd-short-name]

При создании кластера вы можете:

- задать сеть для самого кластера;
- задать подсети для каждого из хостов кластера.

Вы можете создать кластер, не задавая подсети для хостов, если выбранная для каждого хоста зона доступности содержит ровно одну подсеть указанной сети.

## Сетевой доступ к кластеру [!KEYREF mrd-short-name]

Подключиться к кластеру [!KEYREF RD] можно только с той виртуальной машины Облака, которая подключена к той же сети, что и кластер. Получить публичный IP-адрес для хоста в таком кластере невозможно.

## Имя хоста и FQDN {#hostname}

Имя для каждого хоста в кластере [!KEYREF mrd-short-name] генерирует при его создании. Это имя будет являться доменным именем хоста (FQDN). Имя хоста и, соответственно, FQDN невозможно изменить.

FQDN можно использовать для доступа к хосту внутри облачной сети.


# Перемещение данных из бакета Object Storage в ледяное хранилище {#moving-objects-to-glacier-storage-type}

## Задача {#case-description}
Необходимо переместить данные из бакета Object Storage из стандартного или холодного хранилища в ледяное хранилище.

## Решение {#case-solution}
С помощью правил жизненных циклов изменить класс хранения объектов в бакете Object Storage на ледяной пока не получится.

Оптимальным вариантом в этом случае будет скопировать объекты с помощью утилиты AWS CLI в требуемый бакет с указанием параметров хранения, либо с предварительным изменением типа хранения по умолчанию в параметрах бакета.
Для этого необходимо:

1. [Изменить тип хранилища](../../../storage/concepts/storage-class#changing-storage-class) для вашего бакета на ледяное.
2. [Установить и настроить утилиту AWS CLI](../../../storage/tools/aws-cli)
3. Выполнить команду `aws --endpoint-url=https://storage.yandexcloud.net s3 cp --recursive s3:*\<ИМЯ_БАКЕТА>\ s3:*\<ИМЯ_БАКЕТА\>`

{% note info %}

Перед выполнением команды не забудьте заменить `<ИМЯ_БАКЕТА>` на наименование вашего бакета в Object Storage.

{% endnote %}

В этом случае перемещение данных из одного типа хранилища в другое произойдет на стороне Object Storage без необходимости локальной загрузки объектов на хост с установленным AWS CLI.
Также вы можете задать тип хранения для объекта с помощью опции `--storage-class` в AWS CLI:
`aws --endpoint-url=https://storage.yandexcloud.net s3 cp --recursive s3:*\<ИМЯ_БАКЕТА\> s3:*\<ИМЯ_БАКЕТА\> --storage-class GLACIER`

При использовании любого из указанных вариантов смены типа хранения, у объектов в бакете изменится только тип хранилища. 
Дубликаты объектов в бакете в результате этой операции созданы не будут.
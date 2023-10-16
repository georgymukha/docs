# Устранение проблем со сбросом пароля для ВМ на базе образа Kosmos VM


## Описание проблемы {#issue-description}

* При попытке сброитть пароль для учётной записи Administrator из интерфейса консоли управления ничего не происходит.

## Решение {#issue-resolution}

Возможно, в сетевой конфигурации ВМ используются сторонние DNS-сервера, не связанные с Yandex Cloud DNS.
В таком случае следует добавить на этих серверах А-запись вида:
`metadata.google.internal A 169.254.169.254`

Также можно изменить конфигурацию DNS на виртуальных машинах, указав DNS-адрес по умолчанию — второй адрес из используемой для ВМ подсети `(x.x.x.2)`.

## Если проблема осталась {#if-issue-still-persists}

Если вышеописанные действия не помогли решить проблему, [создайте запрос в техническую поддержку]({{ link-console-support }}).
При создании запроса просим указать идентификатор проблемной ВМ и прикрепить ее сетевую конфигурацию в виде текстового вывода или скриншота.
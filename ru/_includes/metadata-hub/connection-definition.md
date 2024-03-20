С помощью {{ connection-manager-full-name }} вы можете управлять параметрами [подключений](../../metadata-hub/concepts/connection-manager.md) к базам данных. Подключения создаются автоматически при создании кластера управляемых баз данных в {{ yandex-cloud }}, если поддержка {{ connection-manager-full-name }} настроена на уровне облака.
Подключения и секреты, которые создаются автоматически при создании кластера, нельзя ни редактировать, ни удалять — они изменяются автоматически при редактировании настроек пользователя в кластере управляемой базы данных.

Подключение содержит всю информацию о параметрах соединения с базой данных. Конфиденциальная часть этой информации, такая как пароль пользователя для доступа к базе данных, хранится в сервисе [{{ lockbox-full-name }}](../../lockbox/index.yaml) в виде [секрета](../../metadata-hub/concepts/secret.md).
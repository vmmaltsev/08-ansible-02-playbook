# Домашнее задание к занятию 2 «Работа с Playbook» - `Мальцев Виктор`

---

Ansible Playbook для установки Clickhouse и Vector

Данный playbook позволяет автоматизированно установить и настроить Clickhouse и Vector на целевых машинах.
Что делает этот playbook?

    Установка Clickhouse:
        Скачивание дистрибутивов Clickhouse.
        Установка пакетов Clickhouse.
        Запуск службы Clickhouse.
        Создание базы данных logs в Clickhouse (если её не существует).

    Установка и настройка Vector:
        Скачивание дистрибутива Vector.
        Установка Vector.
        Деплой конфигурации Vector из шаблона.

Параметры:

    Clickhouse:
        clickhouse_version: версия Clickhouse для установки (например, "22.3.3.44").
        clickhouse_packages: список пакетов Clickhouse для установки. Список формируется автоматически на основе указанной версии.

    Vector:
        vector_version: версия Vector для установки (например, "0.32.0").
        vector_rpm_url: URL для скачивания RPM-пакета Vector. URL формируется автоматически на основе указанной версии.
        vector_config_template: путь к Jinja2-шаблону для генерации конфигурации Vector.
        vector_config_destination: путь к файлу конфигурации Vector на целевой машине.

Теги:

На текущий момент в playbook не используются теги для выполнения конкретных задач. Однако, вы можете добавить их для большей гранулярности управления задачами. Например:

    install: выполнить только задачи установки.
    config: применить только конфигурационные изменения.
    start_services: запустить или перезапустить службы.




Основная часть
Подготовьте свой inventory-файл prod.yml.
Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает vector. Конфигурация vector должна деплоиться через template файл jinja2.
При создании tasks рекомендую использовать модули: get_url, template, unarchive, file.
Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.
Запустите ansible-lint site.yml и исправьте ошибки, если они есть.

Попробуйте запустить playbook на этом окружении с флагом --check.
Запустите playbook на prod.yml окружении с флагом --diff. Убедитесь, что изменения на системе произведены.
Повторно запустите playbook с флагом --diff и убедитесь, что playbook идемпотентен.
Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по ссылке.
Готовый playbook выложите в свой репозиторий, поставьте тег 08-ansible-02-playbook на фиксирующий коммит, в ответ предоставьте ссылку на него.


![alt text](https://github.com/vmmaltsev/screenshot/blob/main/Screenshot_20.png)
![alt text](https://github.com/vmmaltsev/screenshot/blob/main/Screenshot_21.png)
![alt text](https://github.com/vmmaltsev/screenshot/blob/main/Screenshot_22.png)
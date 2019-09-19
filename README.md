
## Предисловие
Добрый день! Мне очень приятно, что вы уделили время моему первому учебному проекту,</br>
надеюсь, вы не потратите свое время впустую.

## Оглавление
* [Постановка задачи](#постановка-задачи)
* [Функционал](#функционал)
* [Компоненты](#компоненты)
* [Инструкция](#инструкция)
* [Выводы](#выводы)

### Постановка задачи
Написать RESTful ToDoList API без использования фрейморков</br>
Все взаимодействие с компонентами проекта производится с использованием командной строки.

### Функционал
* Взаимодействие с логикой API с помощью http запросов
* Хранение в таблице параметров задачи, которую нужно выполнить. Структура таблицы:

| name    | id      | body    | status  |
|---------|---------|---------|---------|
| varchar | varchar | varchar | varchar |

* CRUD методы для контроля операций над содержимым таблицы
* Валидация входных параметров
* Entity Behaviour

### Компоненты
- **Технологии**
	- php 7.2
	- PostgreSQL 10.9
	- Composer
	- Git
- **Использованные библиотеки**
	- Ramsey/Uuid - генерация id в формате Uuid
	- Zend/Diactors - представление request и response в виде объектов
	- Aura/Routing - http mapping
- **Утилиты**
	- httpie 0.9.8 - https://httpie.org/
	- GNU Make 4.2.1

### Инструкция
1. Изменить конфигурацию файла db_configExample.ini
	- Изменить название (db_configExample.ini -> db_config.ini)
	- Изменить его внутренние параметры в соответствии с используемой б\д
2. Создать таблицу для хранения задач при помощи ввода команды утилиты make
	```
	$ make create-table
	```
3. Запустить встроенный в php веб-сервер командой Makefile
	```
	$ make start
	```
4. С помощью утилиты httpie создать http запрос к одному из существующих роутов:
- Добавить задачу
	```
	$ http POST :8000/tasks name=='task name' body=='body content'
	```
- Изменить содержимое задачи
	```
	$ http PUT :8000/tasks/{id}/body/update body=='new body content'
	```
- Изменить статус задачи (возможные статусы: new, in progress, completed)
	```
	$ http PUT :8000/tasks/{id}/status/update status=='in progress'
	```
- Удалить задачу
	```
	$ http DELETE :8000/tasks/{id}
	```
- Вернуть конкретную задачу по ее id
	```
	$ http GET :8000/tasks/{id}
	```
- Вернуть весь список задач
	```
	$ http GET :8000/tasks
	```

### Выводы
В ходе написания моего первого проекта я узнал о следующих вещах:
- *Написание кода и его оформление*
	- Data Hiding
	- Type Hinting
- *Парадигмы и паттерны программирования и проектирования*
	- Named Constructors
	- Data Transfer Object
	- Dependency Injection
	- OOP
	- MVC
	- SOLID
	- REST
	- LIFT
	- CRUD
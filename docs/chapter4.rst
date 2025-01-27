============================================
Прочие (вспомогательные) структуры и функции
============================================

FoundLine
=========

Строка найденной записи, может содержать результат расформатирования найденной записи.

MenuFile и MenuLine
===================

Файл меню. Состоит из пар строк (``MenuLine``).

IniFile, IniSection и IniLine
=============================

INI-файл, состоящий из секций (``IniSection``), которые в свою очередь состоят из строк вида "ключ=значение" (``IniLine``).

TreeFile и TreeLine
===================

TRE-файл -- древовидный справочник.

DatabaseInfo
============

Информация о базе данных ИРБИС.

ProcessInfo
===========

Информация о запущенном на ИРБИС-сервере процессе.

VersionInfo
===========

Информация о версии ИРБИС-сервера.

ClientInfo
==========

Информация о клиенте, подключенном к серверу ИРБИС (не обязательно о текущем).

UserInfo
========

Информация о зарегистрированном пользователе системы (по данным ``client_m.mnu``). Состоит из полей:

============== ========================================
Поле            Назначение
============== ========================================
Number          Номер по порядку в списке.
Name            Логин пользователя.
Password        Пароль.
Cataloger       Доступность АРМ "Каталогизатор".
Reader          Доступность АРМ "Читатель".
Circulation     Доступность АРМ "Книговыдача".
Acquisitions    Доступность АРМ "Комплектатор".
Provision       Доступность АРМ "Книгообеспеченность".
Administrator   Доступность АРМ "Администратор".
============== ========================================

Если строка доступа к АРМ пустая, то доступ к соответствующему АРМ запрещен.

.. code-block:: go

    users := client.GetUserList()
    newUser := UserInfo{Name: "Tyler Durden",
        Password: "Fight Club",
        Cataloger: "INI\\TylerC.ini"}
    users = append(users, newUser)
    client.UpdateUserList(users)


TableDefinition
===============

Данные для метода printTable.

ServerStat
==========

Статистика работы ИРБИС-сервера.

PostingParameters
=================

Параметры для запроса постингов с сервера.

TermParameters
==============

Параметры для запроса терминов с сервера.

TermInfo
========

Информация о термине поискового словаря.

TermPosting
===========

Постинг термина в поисковом индексе.

SearchParameters
================

Параметры для поиска записей (метод SearchEx).

SearchScenario
==============

Сценарий поиска.

ParFile
=======

PAR-файл -- содержит пути к файлам базы данных ИРБИС.

OptFile и OptLine
=================

OPT-файл -- файл оптимизации рабочих листов и форматов показа.

GblStatement и GblSettings
==========================

Поддержка глобальной корректировки базы данных.

ClientQuery
===========

Клиентский запрос. Инфраструктура.

ServerResponse
==============

Ответ сервера. Инфраструктура.

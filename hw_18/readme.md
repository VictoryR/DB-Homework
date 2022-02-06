
Создаем бэкап базы world

![backup](images/18_backup.jpg)
![backup](images/18_backup_2.jpg)


Создаем тестовую базу world_test

![backup](images/18_create_database.jpg)


Подготавливаем бэкап, расшифровываем  и извлекаем из архива обратно

![backup](images/18_backup_3.jpg)

![backup](images/18_backup_4.jpg)

![backup](images/18_backup_5.jpg)


Восстанавливаем структуру базы из дампа

![fill_db](images/18_fill_db.jpg)

Проверям восстановление базы world_test

![show_tables_world_test](images/18_show_tables_world_test.jpg)

Смотрим таблицу city и открепляем tablespace

![desc_city_discard](images/18_desc_city_discard.jpg)

Восстанавливаем таблицу city

![copy_city](images/18_copy_city.jpg)

Добавляем tablespacе

![import_tablespace](images/18_import_tablespace.jpg)

Делаем выборку из таблицы city

![answer](images/18_answer.jpg)

Ответ **189**


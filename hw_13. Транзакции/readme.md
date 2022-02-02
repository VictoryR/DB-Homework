Создаем таблицу load_data для загрузки данных из файла. Загружаем данные


    LOAD DATA INFILE 'C:\\ProgramData\\MySQL\\MySQL Server 8.0\\Uploads\\Bicycles.csv' 
        INTO TABLE load_data
        FIELDS TERMINATED BY ',' ENCLOSED BY '"'
        LINES TERMINATED BY '\n'
        IGNORE 1 LINES;

Посмотрим число записей в таблице

![load_data](images/13_1.png)

И сами записи в таблице

![load_data](images/13_2.png)
       

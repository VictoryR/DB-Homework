
Используем таблицу trainings - история тренировок.

![trainings](images/11_1_1.png)

В таблице 483 записи.

![trainings_count](images/11_1_2.png)

Партиционирование таблицы по годам

    ALTER TABLE trainings PARTITION BY RANGE (year(training_date)) (
        PARTITION p0 VALUES LESS THAN (2020),
        PARTITION p1 VALUES LESS THAN (2021),
        PARTITION p2 VALUES LESS THAN (2022),
        PARTITION p3 VALUES LESS THAN MAXVALUE
    );

Результат выполнения запроса

    SELECT p.PARTITION_NAME, p.TABLE_ROWS FROM INFORMATION_SCHEMA.PARTITIONS p WHERE TABLE_NAME = 'trainings';

![trainings_count](images/11_1_3.png)

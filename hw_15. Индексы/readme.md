Создаем полнотекстовый индекс на тестовой таблице.

    create index pl_last_name_index on test_players (last_name, first_name);

    explain
    select * from test_players
    where test_players.last_name = 'b6e2366d17' && test_players.first_name = 'e4aa1eb258';

без индекса
![load_data](images/15_1_1.png)

с индексом
![load_data](images/15_1_2.png)

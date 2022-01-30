Посчитаем количество игроков по месяцу и году рождения
    
    
    select 
        year(p.date_of_birth) birthYear,
        month(p.date_of_birth) birthMonth,
        count(p.id) as 'Количество игроков'
    from players_new  p
    group by year(p.date_of_birth), month(p.date_of_birth)
    order by birthYear, birthMonth;


Добавим rollup

    select 
        year(p.date_of_birth) birthYear,
        month(p.date_of_birth) birthMonth,
        count(p.id) as 'Количество игроков'
    from players_new  p
    group by year(p.date_of_birth), month(p.date_of_birth) with rollup
    order by birthYear, birthMonth;

Добавим having, выберем игроков моложе 2000 года рождения

    select 
        year(p.date_of_birth) birthYear,
        month(p.date_of_birth) birthMonth,
        count(p.id) as 'Количество игроков'
    from players_new  p
    group by year(p.date_of_birth), month(p.date_of_birth) with rollup
    having birthYear > 1999;

Добавим grouping

    select 
        if(grouping(year(p.date_of_birth)), 'All years', year(p.date_of_birth)) AS birthYear,
        if(grouping(month(p.date_of_birth)), 'All months', month(p.date_of_birth)) AS birthMonth,
        count(p.id) as 'Количество игроков'
    from players_new p
    group by year(p.date_of_birth), month(p.date_of_birth) with rollup
    order by birthYear desc, birthMonth desc;

Найдем максимальный рост игроков на каждой позиции

    select 
        p.role_id roleId,
        max(p.height) as playerHeight
    from players_new  p
    group by p.role_id;

Найдем минимальный вес игроков на каждой позиции

    select 
        p.role_id roleId,
        min(p.weight) as playerWeight
    from players_new  p
    group by p.role_id;
   
    
    
    
    

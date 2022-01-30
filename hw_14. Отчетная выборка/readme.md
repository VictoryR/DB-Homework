Посчитаем количество игроков по дням рождениям по месяцам и годам.
    
    
    select 
        year(p.date_of_birth) birthYear,
        month(p.date_of_birth) birthMonth,
        count(p.id) as 'Количество игроков'
    from players_new  p
    group by year(p.date_of_birth), month(p.date_of_birth)
    order by birthYear, birthMonth;

Создадим процедуру get_statistic. 

    DELIMITER $$
    USE `otus`$$
    CREATE PROCEDURE get_statistic (IN matchYear char(4), IN matchTournament int)
    BEGIN
        select 
            m.rival_name as rivalName,
            count(
            CASE 
                    WHEN m.rival_score > m.score THEN  m.id 
                END) as lostMatches,
            sum(m.rival_score) as 'Общее число очков соперника',
            sum(m.score) as 'Число очков команды'
        from matches_new m
        where year(m.match_date) = matchYear and m.tournament_id = matchTournament
        group by rivalName
        order by lostMatches desc;
    END$$
    DELIMITER ;
    
    
    call get_statistic('2020', 16);



    delimiter $$
    use `otus`$$
    create procedure get_statistic_new (in matchYear char(4), IN matchTournament int, in orderBy char(20), in orderSort char(4), in pagerOffer int,
    IN pagerLimit int)
    begin
        set @query = CONCAT('
            select 
            m.rival_name as rivalName,
            count(
            CASE 
                    WHEN m.rival_score > m.score THEN  m.id 
                END) as lostMatches,
            sum(m.rival_score) as rivalScore,
            sum(m.score) as score
            from matches_new m
            where year(m.match_date) = ',matchYear,' and m.tournament_id = ',matchTournament,'
            group by rivalName
            order by ',orderBy,' ',orderSort,'
            limit ',pagerLimit,', ',pagerOffer,';'
        );
        prepare SQL_QUERY from @query;
        execute SQL_QUERY;
    end$$
    delimiter ;
    
    call get_statistic_new('2020', 16, 'score', 'desc', 3 , 1);


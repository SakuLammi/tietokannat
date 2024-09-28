# 03 yhteen tauluun kohdistuvat kyselyt

### Tehtävä 1
SELECT * FROM goal; 
![image](https://github.com/user-attachments/assets/51507889-0bef-45fa-85dd-899e543d2021)


### Tehtävä 2
select name, type from airport where iso_country = "FI";' 
![image](https://github.com/user-attachments/assets/c0dfdc31-2427-4dd1-9d16-ee37636088e5)


### Tehtävä 3
select name from airport where iso_country = "FI" order by name;
![image](https://github.com/user-attachments/assets/9ca76f4c-bf17-4165-8df3-c0921dd69977)


### Tehtävä 4
select name, `type` from airport where iso_country = "FI" order by type, name;
![image](https://github.com/user-attachments/assets/2137dd20-5c20-40e9-897a-81a4088e13e9)


### Tehtävä 5 	
select name from country where name like "F%";
![image](https://github.com/user-attachments/assets/cbbec77a-b79f-4e52-9902-90e07275a953)


### Tehtävä 6
select name from country where name like "%F%";
![image](https://github.com/user-attachments/assets/c23caeaa-56b4-4542-9063-17e871527cde)


### Tehtävä 7
select location from game where screen_name = "Vesa";
![image](https://github.com/user-attachments/assets/7a497c61-17c0-4977-81b5-f353c378115a)


### Tehtävä 8
select co2_consumed from game where screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/9dd2b28a-bc0b-464b-bd87-824c9a8743e0)


### Tehtävä 9
select distinct co2_budget from game;
![image](https://github.com/user-attachments/assets/366a79f0-b675-44a4-90f6-beee31232792)


# 04 where-osan liitosehto

### Tehtävä 1
select country.name as "country name", airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "Iceland";
![image](https://github.com/user-attachments/assets/fa8c7df0-4923-4476-aace-bb9f5edeb961)


### Tehtävä 2
select airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "France" and airport.type = "large_airport";
![image](https://github.com/user-attachments/assets/20f01ce3-5669-4814-a152-271060535a73)


### Tehtävä 3
select country.name as country_name, airport.name as airport_name
from airport, country
where airport.iso_country = country.iso_country and country.continent = "AN";
![image](https://github.com/user-attachments/assets/a8a3a0cb-fb6a-4974-98f4-af42459f9427)


### Tehtävä 4
select elevation_ft
from airport, game
where location = ident and screen_name = "Heini";
![image](https://github.com/user-attachments/assets/33aa2382-91f4-45b5-9f28-ea36d29cd3cc)


### Tehtävä 5
select elevation_ft * 0.3048 as elevation_m
from airport, game
where location = ident and screen_name = "Heini";
![image](https://github.com/user-attachments/assets/1b76bad1-63bd-4c7f-933f-188cf6612402)


### Tehtävä 6
select name
from airport, game
where location = ident and screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/47fa4747-c488-4c10-9777-3a3ca0c69605)


### Tehtävä 7
select country.name
from airport, game, country
where location = ident and airport.iso_country = country.iso_country  and screen_name = "Ilkka";
![image](https://github.com/user-attachments/assets/ffb77a6e-96b3-46f9-bf22-8dea45791e50)


### Tehtävä 8
select name
from goal, goal_reached, game
where game.id = game_id and goal.id = goal_id and screen_name = "Heini";
![image](https://github.com/user-attachments/assets/9d9d954b-1507-4b3b-9cf8-ab50d3d7e27a)


### Tehtävä 9
select airport.name
from airport, game, goal, goal_reached
where ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";
![image](https://github.com/user-attachments/assets/ae2db498-07d7-46dd-9dfd-ef93b5d6b65c)


### Tehtävä 10
select country.name
from country, airport, game, goal, goal_reached
where airport.iso_country = country.iso_country and ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";
![image](https://github.com/user-attachments/assets/669c59a5-5fe1-49d1-8e50-726129c94a99)


# 05 Join

### Tehtävä 1
select country.name as "country name", airport.name as "airport name"
from country inner join airport on airport.iso_country = country.iso_country
where country.name = "Finland" and scheduled_service = "yes";
![image](https://github.com/user-attachments/assets/7df6aa94-22d9-4da4-99c3-36f13a903ba4)


### Tehtävä 2
select screen_name, airport.name
from game inner join airport on location = ident;
![image](https://github.com/user-attachments/assets/e6f5fa6d-4179-4c62-bfd4-56b132f2e414)


### Tehtävä 3
select screen_name, country.name
from game inner join airport on location = ident inner join country on airport.iso_country = country.iso_country;
![image](https://github.com/user-attachments/assets/3c4cb061-3414-4de2-a313-ef4db052745c)


### Tehtävä 4
select airport.name, screen_name
from airport left join game on ident = location where name like "%Hels%";
![image](https://github.com/user-attachments/assets/7ce05f24-7f68-4108-b6f4-d58d1f657b5a)


### Tehtävä 5
select name, screen_name
from goal left join goal_reached on goal.id = goal_id  left join game on game.id = game_id;
![image](https://github.com/user-attachments/assets/a16bcd03-7517-4794-9285-f48ee02e9bda)


# 06 Sisäkyselyt

### Tehtävä 1
select name
from country
where iso_country in(
select iso_country
from airport
where name like "Satsuma%"
);
![image](https://github.com/user-attachments/assets/b37e9724-1c0f-426c-8a1d-560e94bf5ebd)


### Tehtävä 2
select name
from airport where
iso_country in(
select iso_country
from country
where name = "Monaco"
);
![image](https://github.com/user-attachments/assets/e20cc09d-50f4-41ac-82b0-b8550e9f2ea5)


### Tehtävä 3
select screen_name
from game
where id in (
select game_id
from goal_reached
where goal_id in(
select id
from goal
where name = "CLOUDS"
)
);

![image](https://github.com/user-attachments/assets/f53dd98c-4f38-4e0d-be84-0a4fc60c230c)


### Tehtävä 4
select country.name
from country
where iso_country not in
(select airport.iso_country
from airport);
![image](https://github.com/user-attachments/assets/e402a373-6aae-4cf7-a612-0683f363b6fa)


### Tehtävä 5
select name
from goal
where id not in(
select goal.id
from goal, goal_reached, game
where game.id = game_id and goal.id = goal_id and screen_name = "Heini"
);
![image](https://github.com/user-attachments/assets/6289828d-ab75-4840-a4f9-bc1a095cee63)


# 07 Koostetietokyselyt

### Tehtävä 1
select max(elevation_ft)
from airport;
![image](https://github.com/user-attachments/assets/26c4c5c2-9545-4cde-860e-02113203b905)


### Tehtävä 2
select continent, count(*)
from country
group by continent;
![image](https://github.com/user-attachments/assets/4148b216-135d-4e0a-8e6e-bee212c73db7)


### Tehtävä 3
select screen_name, count(*)
from game, goal_reached
where id = game_id
group by screen_name;
![image](https://github.com/user-attachments/assets/7c34e275-4bf7-4169-a858-02f995cfdac4)


### Tehtävä 4
select screen_name
from game
where co2_consumed in(
select min(co2_consumed)
from game
);
![image](https://github.com/user-attachments/assets/efc5de36-c86b-4d1e-a470-29e0eb001f8d)


### Tehtävä 5
select country.name, count(*)
from airport, country
where airport.iso_country = country.iso_country
group by country.iso_country
order by count(*) desc
limit 50;
![image](https://github.com/user-attachments/assets/0a2844d8-ec59-43d2-b958-dae2f1352c05)


### Tehtävä 6
select country.name
from airport, country
where airport.iso_country = country.iso_country
group by country.iso_country
having count(*) > 1000;
![image](https://github.com/user-attachments/assets/99d8210e-352e-4cfb-8798-ee63b8eec410)


### Tehtävä 7
select name
from airport
where elevation_ft in (
select max(elevation_ft)
from airport
);
![image](https://github.com/user-attachments/assets/6759070b-ab70-4ba6-a310-f20ddef8b7ab)


### Tehtävä 8
select name
from country
where iso_country in (
select iso_country
from airport
where elevation_ft in(
select max(elevation_ft)
from airport
)
);
![image](https://github.com/user-attachments/assets/660c62a2-0a25-4bc5-ad84-60e876a80ccf)


### Tehtävä 9
select count(*)
from game, goal_reached
where id = game_id and screen_name = "Vesa"
group by screen_name;
![image](https://github.com/user-attachments/assets/2d031659-4e84-4f7b-a58d-d2ef9d818ac8)


### Tehtävä 10
select name
from airport
where latitude_deg in(
select min(latitude_deg)
from airport
);
![image](https://github.com/user-attachments/assets/b86cfabd-172e-4701-883c-324a022f00d2)


# 08 Päivityskyselyt

### Tehtävä 1
update game
set  location = (select ident from airport where name = "Nottingham Airport"), co2_consumed = co2_consumed+500
where screen_name = "Vesa";

select * from game;
![image](https://github.com/user-attachments/assets/1e42c184-ee92-4041-b4de-26a7c8b3755f)


### Tehtävä 2
goal_reached


### Tehtävä 3
delete from goal_reached;
select * from goal_reached;
![image](https://github.com/user-attachments/assets/be7268be-a9e0-4516-9e2e-96c9a537f0a5)


### Tehtävä 4
delete from game;
select * from game;
![image](https://github.com/user-attachments/assets/163ac0e5-e037-4158-afa8-53cd81b6ca27)

# Tietokannan suunnittelu harjoitukset

### Tehtävä 1
airport on suorakulmainen


### Tehtävä 2
airport


### Tehtävä 3
a


### Tehtävä 4
tosi


### Tehtävä 5
tosi


### Tehtävä 6
c


### Tehtävä 7
b


### Tehtävä 8
tosi


### Tehtävä 9
b


### Tehtävä 10
b


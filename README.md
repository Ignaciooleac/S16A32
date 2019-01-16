## Actividad 32 - Postgresql Avanzado

# Query #1
CREATE DATABASE pintagram;
# Query #2
CREATE TABLE users (id SERIAL PRIMARY KEY, first_name VARCHAR(64));
# Query #3
CREATE TABLE images (id int PRIMARY KEY, name VARCHAR(64), owner_id int REFERENCES users(id));
# Query #4
CREATE TABLE tags (id int PRIMARY KEY, name VARCHAR(64));
# Query #5
CREATE TABLE taggin (id int PRIMARY KEY, tag_id int REFERENCES tags(id), image_id int REFERENCES images(id));
# Query #6
CREATE TABLE evaluate_post (id int PRIMARY KEY, user_id int REFERENCES users(id), image_id int REFERENCES images(id), liked BOOLEAN );
# Query #7
INSERT INTO images (id, name, owner_id) VALUES ('1', 'Beach', '1');


INSERT INTO images (id, name, owner_id) VALUES ('2', 'Digital', '1';


INSERT INTO images (id, name, owner_id) VALUES ('3', 'ART', '2');


INSERT INTO images (id, name, owner_id) VALUES ('4', 'SPACE', '2');


INSERT INTO images (id, name, owner_id) VALUES ('5', 'Memes', '3');


INSERT INTO images (id, name, owner_id) VALUES ('6', 'Food', '3');
# Query #8
INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('1','1','1','false');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('1','2','1','false');

DETAIL:  Key (id)=(1) already exists.
INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('2','2','1','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('2','1','1','true');

DETAIL:  Key (id)=(2) already exists.
INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('3','1','1','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('4','1','2','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('5','2','2','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('6','3','2','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('7','1','3','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('8','2','3','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('9','3','3','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('10','1','4','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('10','1','4','true');

DETAIL:  Key (id)=(10) already exists.
INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('11','2','4','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('12','3','4','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('13','1','5','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('14','2','5','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('15','3','5','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('16','1','6','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('17','2','6','true');

INSERT INTO evaluate_post (id, user_id, image_id, liked) VALUES ('18','3','6','true');
# Query #9
INSERT INTO tags (id, name) VALUES ('1', 'Happy');

INSERT INTO tags (id, name) VALUES ('2', 'Birthday');

INSERT INTO tags (id, name) VALUES ('3', 'Peace');

INSERT INTO tags (id, name) VALUES ('4', 'Mayonaise');

INSERT INTO tags (id, name) VALUES ('5', 'PC');

INSERT INTO tags (id, name) VALUES ('6', 'Killme');

INSERT INTO tags (id, name) VALUES ('7', 'Random');

INSERT INTO tags (id, name) VALUES ('8', 'Japan');
# Query #10
INSERT INTO taggin (id, image_id, tag_id) VALUES ('1', '1', '1');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('2', '1', '1');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('3', '1', '3');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('4', '1', '5');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('5', '2', '5');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('6', '2', '8');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('7', '2', '1');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('8', '3', '4');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('9', '3', '7');

INSERT INTO taggin (id, image_id, tag_id) VALUES ('10', '3', '3');

# Query #11
select i.name, count(e.id) from images i join evaluate_post e on e.image_id = i.id where e.liked = TRUE group by i.name;

  name   | count 
---------+-------
 SPACE   |     3
 ART     |     3
 Beach   |     2
 Memes   |     3
 Digital |     3
 Food    |     3
(6 rows)

# Query #12
select u.first_name,i.name from users u join images i on i.owner_id = u.id;

 first_name |  name   
------------+---------
 Carlos     | Beach
 Carlos     | Digital
 Laura      | ART
 Laura      | SPACE
 Ignacio    | Memes
 Ignacio    | Food

# Query #13
SELECT name, count(Taggin.id) as "Cantidad de tags" FROM Tags, Taggin WHERE Tags.id = Taggin.id GROUP BY (name,tag_id);

   name    | Cantidad de tags 
-----------+------------------
 Japan     |                1
 Mayonaise |                1
 Random    |                1
 Birthday  |                1
 Happy     |                1
 PC        |                1
 Peace     |                1
 Killme    |                1
(8 rows)

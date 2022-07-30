# Image-Nation-PrideHacks

We advise to install first  XAMMP (a package to install apache + mariaDB + php in one!)
Visit https://www.apachefriends.org/ for more information.

Then execute the SQL script that will create tables.

![Alt text](images/imagenation_schema.png?raw=true "Schema")

# ========= Main tables =========

### Artists
 
Any artists linked with movies. The table role explains what role any artistis doing in a movie.
The biography table allows to have a biography by language by artist.
Artists_statement table allow to have a statement by language by artist.
Artist can have many media (see artist_media table).
Artist region links are describe in region table.
fct_cultural_identities, fct_gender_identities, fct_sexual_identities are reference table to categoryze artist.

### Movie
 
All movie in the database.
A movie could be linked to many type of media: poster, picture, trailer... for that we have a movie_media table the type explain what media is.
A movie can have one or more genres (see the tables genre and genre_name)
A movie can be produce in one or more region, see production for that.
The region table allow 3 level of granularity: country level, division level (like states for US or province for Canada, department, canton for Switzerland) and the town level.

A tag can be anything to decribe either way artists or movie see tag table.

# ========= Sample queries =========
 
#### Find all movies with tag Child:

SELECT tn.tag_text , m.name_original , m.year_release
<br>FROM tag_name tn, tag t, movie m
<br>WHERE tn.tag_name_id  = t.tag_name_id AND t.movie_id = m.movie_id
and tn.tag_text = 'Child';



#### Find artists linked to Montreal:

SELECT  m.name_original , m.year_release, n.town_fr
<br>FROM region_name rn, region r, artists a  
<br>WHERE rn.town_fr = 'Montreal'
and rn.region_name_id  = r.region_name_id
and r.artist_id = a.artist_id ;


#### Find all drama movies:

SELECT m.name_original , m.year_release , gn.genre_name_fr
<br>FROM genre_name gn, genre g, movie m
<br>WHERE genre_name_fr = 'Drame'
and gn.genre_name_id = g.genre_name_id
;


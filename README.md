# Image-Nation-PrideHacks

We preconize to install first  XAMMP (a package to install apache + mariaDB + php in one!
https://www.apachefriends.org/

Then execute the SQL script that will create tables.


=========  Main tables  ==================

Artists
-------
Any artists in link with movies. The table role explain what role any artist is doingin a movie
The biographie table allow to have a biographie by langage by artist.
Artists_statement table allow to have a statement by langage by artist.
Artist can have many media (see artist_media table).
fct_cultural_identities, fct_gender_identities, fct_sexual_identities are reference table to categoryze artist.

Movie
-------
All movie in the database.
A movie could be linked to many type of media: poster, picture, trailer... for that we have a movie_media table the type explain what media is.
A movie can have 1 or more genre (see genre table and genre_name)

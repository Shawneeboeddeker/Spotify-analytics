# Spotify-analytics
For this project, I downloaded Spotify data from Kaggle. Then I created a table to insert Spotify data into. I then performed analytics on the data using SQL.

/* For this project, I downloaded Spotify data from Kaggle. Then I created a table to insert Spotify data into. I then performed analytics on the data using SQL.*/

/*Creation of the table*/

CREATE TABLE BIT_DB.Spotifydata (
id integer PRIMARY KEY,
artist_name varchar NOT NULL,
track_name varchar NOT NULL,
track_id varchar NOT NULL,
popularity integer NOT NULL,
danceability decimal(4,3) NOT NULL,
energy decimal(4,3) NOT NULL,
song_key integer NOT NULL,
loudness decimal(5,3) NOT NULL,
song_mode integer NOT NULL,
speechiness decimal(5,4) NOT NULL,
acousticness decimal(6,5) NOT NULL,
instrumentalness decimal(8,7) NOT NULL,
liveness decimal(5,4) NOT NULL,
valence decimal(4,3) NOT NULL,
tempo decimal(6,3) NOT NULL,
duration_ms integer NOT NULL,
time_signature integer NOT NULL );

/*I inserted the Spotify Data .csv into the above table*/

SELECT * FROM Spotifydata;

/*Spotify analysis on popular songs from 2021*/

/*#1 What is the average popularity?*/

SELECT AVG(popularity)
FROM BIT_DB.Spotifydata;
/*86.8*/

/*#2 What are the songs and artists with a popularity > 86.8?*/
SELECT artist_name, track_name, popularity
FROM BIT_DB.Spotifydata
WHERE popularity > '86.6'
GROUP BY artist_name
ORDER BY popularity desc;
/* Ed Sheeran Bad Habits*/

/*#3 Who has an above average popular song that has above average energy?*/
SELECT AVG(energy)
FROM BIT_DB.Spotifydata;
/*0.64636*/
/*After seeing how many artist had so many songs at high energy  I raised the energy level to .80

SELECT artist_name, track_name, popularity, energy
FROM BIT_DB.Spotifydata
WHERE popularity > '86.6'
AND energy > '0.80'
GROUP BY artist_name
ORDER BY popularity desc;
/*Ed Sheeran's Bad Habits wins for both most popular and energetic*/

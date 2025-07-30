# 🎵 Music Analysis Using SQL
![image alt](https://github.com/nandeepalva468/Music_Analysis_SQL/blob/4cc39c0e340a0583c447c312e999746dda1fa83b/Spotify.jpg)

**📊 Level:** Advanced  
**🗃️ Database:** `SPOTIFY_DB`  
**👨‍💻 Author:** [nandeepalva468](https://github.com/nandeepalva468)

---

Welcome to the **Music Dataset SQL Analysis** project! This project showcases how SQL can be used to explore and analyze real-world music streaming data. Perfect for beginners looking to practice SQL with structured examples.

---

## 📥 Dataset

You can download the dataset from Kaggle or the GitHub repository:

🔗 [**Spotify Dataset on Kaggle**](https://www.kaggle.com/datasets/sanjanchaudhari/spotify-dataset)

---

## 🎯 Objectives

- ✅ Create and populate the `spotify` table  
- 🧹 Clean and preprocess raw music data  
- 🔍 Perform exploratory data analysis (EDA)  
- 💡 Answer streaming trends and behavior-based questions using SQL

---

## 🧱 Database Structure

The project uses a single table called `spotify` with the following columns:

| Column Name         | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `artist`            | Name of the music artist                                                    |
| `track`             | Title of the individual song or track                                       |
| `album`             | Album to which the track belongs                                            |
| `album_type`        | Type of album (`single`, `album`, etc.)                                     |
| `danceability`      | Danceability score of the track (0.0 to 1.0)                                |
| `energy`            | Energy level of the track (0.0 to 1.0)                                      |
| `loudness`          | Loudness level in decibels                                                  |
| `speechiness`       | Speechiness of the track (0.0 to 1.0)                                       |
| `acousticness`      | Acoustic quality of the track (0.0 to 1.0)                                  |
| `instrumentalness`  | Instrumentalness score (0.0 to 1.0)                                         |
| `liveness`          | Liveness score representing presence of audience                            |
| `valence`           | Positivity or musical cheerfulness (0.0 to 1.0)                             |
| `tempo`             | Tempo in beats per minute (BPM)                                             |
| `duration_min`      | Duration of the track in minutes                                            |
| `title`             | YouTube or display title of the video                                       |
| `channel`           | Channel name on YouTube or streaming platform                               |
| `views`             | Total number of views on YouTube                                            |
| `likes`             | Total number of likes                                                       |
| `comments`          | Number of user comments                                                     |
| `licensed`          | Indicates whether the track is licensed (`TRUE` / `FALSE`)                  |
| `official_video`    | Indicates whether the video is an official release (`TRUE` / `FALSE`)       |
| `stream`            | Total number of streams (Spotify or other platforms)                        |
| `energy_liveness`   | Combined score of energy and liveness for mood analysis                     |
| `most_played_on`    | Platform or region where the track is most streamed (e.g., `Spotify`, `India`) |

---

## 🧹 Data Cleaning & Preprocessing

Before analysis, we performed the following data cleaning and preprocessing steps to ensure accuracy and consistency:

### ✅ Null Handling

- Removed rows where any of the critical columns (`artist`, `track`, `album`, `views`, `likes`, `stream`, etc.) had `NULL` values.
```sql
DELETE FROM spotify
WHERE artist IS NULL OR track IS NULL OR album IS NULL OR
      views IS NULL OR likes IS NULL OR stream IS NULL;
```
### 1. Database Setup

```sql
CREATE DATABASE SPOTIFY_DB;
```
### 2. Table Creation
```sql
DROP TABLE IF EXISTS spotify;
CREATE TABLE spotify (
    artist VARCHAR(255),
    track VARCHAR(255),
    album VARCHAR(255),
    album_type VARCHAR(50),
    danceability FLOAT,
    energy FLOAT,
    loudness FLOAT,
    speechiness FLOAT,
    acousticness FLOAT,
    instrumentalness FLOAT,
    liveness FLOAT,
    valence FLOAT,
    tempo FLOAT,
    duration_min FLOAT,
    title VARCHAR(255),
    channel VARCHAR(255),
    views FLOAT,
    likes BIGINT,
    comments BIGINT,
    licensed BOOLEAN,
    official_video BOOLEAN,
    stream BIGINT,
    energy_liveness FLOAT,
    most_played_on VARCHAR(50)
);
```
### 3.Data Cleaning
```sql
-- Remove rows with NULLs in important fields
SELECT FROM spotify
WHERE artist IS NULL OR track IS NULL OR album IS NULL OR
      album_type IS NULL OR danceability IS NULL OR energy IS NULL OR
      loudness IS NULL OR speechiness IS NULL OR acousticness IS NULL OR
      instrumentalness IS NULL OR liveness IS NULL OR valence IS NULL OR
      tempo IS NULL OR duration_min IS NULL OR title IS NULL OR
      channel IS NULL OR views IS NULL OR likes IS NULL OR
      comments IS NULL OR licensed IS NULL OR official_video IS NULL OR
      stream IS NULL OR energy_liveness IS NULL OR most_played_on IS NULL;
```
### 4.Delete if there is an NULL
```sql
DELETE FROM spotify
WHERE artist IS NULL OR track IS NULL OR album IS NULL OR
      album_type IS NULL OR danceability IS NULL OR energy IS NULL OR
      loudness IS NULL OR speechiness IS NULL OR acousticness IS NULL OR
      instrumentalness IS NULL OR liveness IS NULL OR valence IS NULL OR
      tempo IS NULL OR duration_min IS NULL OR title IS NULL OR
      channel IS NULL OR views IS NULL OR likes IS NULL OR
      comments IS NULL OR licensed IS NULL OR official_video IS NULL OR
      stream IS NULL OR energy_liveness IS NULL OR most_played_on IS NULL;
```
### SQL Questions(EASY LEVEL)
1. Retrieve the names of all tracks that have more than 1 billion streams.
```sql
select * from spotify
where stream > 1000000000;
```

2. List all albums along with their respective artists.
```sql
select album,artist from spotify;

select * from spotify 
where artist='Kendrick Lamar';
```

3. Get the total number of comments for tracks where `licensed = TRUE`.
```sql
select sum(comments) as total_comments from spotify
where licensed='true';
```

4. Find all tracks that belong to the album type `single`.
```sql
select * from spotify
where album_type='single';
```

5. Count the total number of tracks by each artist.
```sql
select artist,count(*) as total_songs  from spotify
group by artist;
```



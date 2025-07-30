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


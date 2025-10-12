# 🎵 Sparkify Data Warehousing Project

> **Note:** This is an assignment repository for the **SMIT Cloud Data Engineering (Batch 2)** program.

This project focuses on building a scalable data warehouse using **Snowflake** for Sparkify, a fictional music streaming startup. The goal is to design an optimized star schema, perform ETL operations, and enable efficient analytical queries on user activity and song metadata.

---

## 📁 Project Structure

```
Sparkify-data-warehousing/
│
├── README.md                 # Project documentation
├── images/                   # Architecture and schema diagrams
│   ├── architecture.PNG
│   └── schema.PNG
└── data/
    ├── log_data/             # User activity event logs (JSON)
    │   ├── 2018-11-01-events.json
    │   ├── 2018-11-02-events.json
    │   └── ...
    └── song_data/            # Song metadata (JSON)
        └── A/
            ├── A/
            └── B/
```


## 🎶 Datasets Description

The project uses two JSON datasets — **Song Data** and **Log Data (Events)** — which simulate real activity from the Sparkify app.

### 1. Song Data

Each file contains metadata about a single song and its artist.

**Example Structure:**

```json
{
  "num_songs": 1,
  "artist_id": "ARJIE2Y1187B994AB7",
  "artist_latitude": null,
  "artist_longitude": null,
  "artist_location": "",
  "artist_name": "Line Renaud",
  "song_id": "SOUPIRU12A6D4FA1E1",
  "title": "Der Kleine Dompfaff",
  "duration": 152.92036,
  "year": 0
}
```

**Key Fields:**

| Field | Description |
|-------|-------------|
| `song_id` | Unique song identifier |
| `title` | Song title |
| `artist_id` | Foreign key reference to artist |
| `artist_name` | Artist name |
| `year` | Song release year |
| `duration` | Song duration in seconds |

### 2. Log Data (Event Data)

Contains user activity logs (e.g., songs played, user sessions).

**Example Structure:**

```json
{
  "artist": "Pavement",
  "auth": "Logged In",
  "firstName": "Sylvie",
  "gender": "F",
  "itemInSession": 0,
  "lastName": "Cruz",
  "length": 99.16036,
  "level": "free",
  "location": "Washington-Arlington-Alexandria, DC-VA-MD-WV",
  "method": "PUT",
  "page": "NextSong",
  "registration": 1540266185796.0,
  "sessionId": 345,
  "song": "Mercy:The Laundromat",
  "status": 200,
  "ts": 1541990258796,
  "userAgent": "\"Mozilla/5.0 ...\"",
  "userId": "10"
}
```

**Key Fields:**

| Field | Description |
|-------|-------------|
| `userId` | Unique user ID |
| `firstName`, `lastName`, `gender` | User details |
| `level` | User subscription level (free/paid) |
| `song`, `artist`, `length` | Song being played |
| `sessionId` | Session ID for the event |
| `location` | User location |
| `ts` | Timestamp (in milliseconds) |

---

## 🧩 Data Model (Star Schema)

The warehouse schema is designed as a **star schema** optimized for song-play analysis.

### Fact Table

- **`songplays`** – Records in log data associated with song plays.

### Dimension Tables

- **`users`** – Users of the Sparkify app.
- **`songs`** – Songs in the music database.
- **`artists`** – Artists who performed the songs.
- **`time`** – Timestamps of records broken down into units (hour, day, week, etc.).

---

## ETL Workflow Summary

### 1. **Extract**
   - Data is read from S3 buckets (`song_data`, `log_data`).

### 2. **Transform**
   - JSON data is cleaned and structured into fact and dimension tables.

### 3. **Load**
   - Data is inserted into Snowflake tables for analytics.

---

##  Learning Objectives

- Build a cloud-based data warehouse using **Snowflake**.
- Design an optimized **star schema** for analytical queries.
- Develop **ETL pipelines** to automate extraction, transformation, and loading.
- Understand **data modeling** and **metadata management** in cloud environments.

---

## Getting Started

### Prerequisites
- Python 3.x
- Snowflake account
- AWS account (for S3 access)
- Required Python packages (install via `requirements.txt`)

### Setup
1. Configure `dwh.cfg` with your Snowflake and AWS credentials.
2. Run `create_tables.py` to set up the database schema.
3. Run `etl.py` to execute the ETL pipeline.

---

## Project Assignment

This project is part of the **SMIT Cloud Data Engineering (Batch 2)** curriculum and demonstrates practical implementation of data warehousing concepts using modern cloud technologies like **Snowflake** and **AWS S3**.

---

## License

This is an educational project for learning purposes.
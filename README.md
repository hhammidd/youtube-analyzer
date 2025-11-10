# 🧠 Ploutube Analyzer  
### YouTube Channel & Video Data Analyzer

Ploutube Analyzer is a modular system for fetching, storing, and analyzing YouTube data — including channels, videos, topics, and metrics.  
It’s designed for creators, analysts, and developers who want to explore YouTube trends programmatically.

---

## 🚀 Features
- Fetch and store YouTube channel data (title, stats, metadata)  
- Collect new video information using RSS feeds  
- Track video performance metrics (views, likes, comments) over time  
- Organize topics and keywords for analysis  
- Scalable design — add new topics easily (e.g. TRAVEL_EN, MUSIC_EN, etc.)  
- Compatible with PostgreSQL and YouTube Data API  

---

## 🧩 Project Structure

```
ploutube_analyzer/
│
├── travel_en/
│   ├── yt_travel_en_channels_fetch.py
│   ├── yt_travel_en_channels_detail.py
│   ├── rss_travel_en_monitor.py
│   ├── update_travel_en_videos_snapshots_metrics.py
│   ├── logs/
│   └── README.md
│
├── sql/
│   ├── create_tables.sql
│   └── seed_keywords.sql
│
├── .env.example
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/ploutube-analyzer.git
cd ploutube-analyzer
```

### 2. Create a Virtual Environment
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Create a `.env` file based on the provided `.env.example`:

```
# Example only — do NOT commit real credentials
YOUTUBE_API_KEY_TRAVEL_EN=your_api_key_here
DATABASE_URL=postgresql://user:password@hostname:5432/ploutube_db
```

🛑 **Important:** Never commit your real `.env` file or credentials to GitHub.  
You can add `.env` to `.gitignore` to keep it private.

---

## 🗄️ Database Setup

1. Create a PostgreSQL database (local or remote).  
2. Run the SQL scripts in `sql/create_tables.sql` to initialize tables.  
3. Optionally seed keyword data from `sql/seed_keywords.sql`.

Example:
```bash
psql -d ploutube_db -f sql/create_tables.sql
```

---

## 🧠 Workflow Overview

### 1. Define a Topic
Create a new folder (e.g. `travel_en`) for each topic.  
Inside, you’ll maintain Python scripts for fetching channels, videos, and metrics.

### 2. Fetch Channels
Run the initial script to collect channels by keyword:
```bash
python travel_en/yt_travel_en_channels_fetch.py
```

### 3. Get Detailed Channel Info
```bash
python travel_en/yt_travel_en_channels_detail.py
```

### 4. Monitor RSS Feeds for New Videos
```bash
python travel_en/rss_travel_en_monitor.py
```

### 5. Update Video Metrics
```bash
python travel_en/update_travel_en_videos_snapshots_metrics.py
```

---

## 🕒 Automation (Optional)

You can schedule recurring tasks using **cron jobs** or any task scheduler.  
Example cron syntax (safe placeholders):

```
# Run RSS monitor hourly
10 * * * * cd /path/to/ploutube_analyzer/travel_en && /path/to/venv/bin/python rss_travel_en_monitor.py >> logs/rss_monitor.log 2>&1

# Update metrics hourly
50 * * * * cd /path/to/ploutube_analyzer/travel_en && /path/to/venv/bin/python update_travel_en_videos_snapshots_metrics.py >> logs/update_metrics.log 2>&1
```

*(Do not expose your actual server path or username in public examples.)*

---

## 📦 Requirements

- Python 3.9+  
- PostgreSQL 13+  
- YouTube Data API v3  
- Recommended Python packages:
  ```
  psycopg2
  google-api-python-client
  python-dotenv
  feedparser
  ```

---

## 🧰 Developer Notes

- All scripts are modular; you can duplicate any topic folder (e.g., `MUSIC_EN`) and adjust table names.  
- Add or edit SQL schemas in `/sql/` for new modules.  
- Use environment variables for all secrets.  
- Ensure directories like `/logs` exist before running jobs.  

---

## 🧠 Security & Privacy
- **Never** commit API keys, credentials, or `.env` files.  
- Do not publish your database URLs or IP addresses.  
- All sample SQL and cron commands in this repo use **safe placeholders**.  

---

## 🤝 Contributing
Pull requests are welcome!  
If you’d like to add support for a new YouTube topic or feature, please open an issue or submit a PR.

---

## 📬 Contact
For demos, API integration, or collaboration inquiries, visit  
👉 [www.ploutube.com](#) *(or your future site)*  
or email **contact@ploutube.com**

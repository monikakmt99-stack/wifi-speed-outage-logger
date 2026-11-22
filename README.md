# NetPulse — Wi-Fi Speed & Outage Logger

A full-stack Python and Flask web application that continuously monitors your internet connection, logs speed metrics (Download, Upload, Ping) and network outages into an SQLite database, and displays real-time analytics on a dark-mode web dashboard[cite: 1].

---

## Key Features

- **Automatic Outage Detection:** Performs a fast TCP socket check (`8.8.8.8:53`) before running bandwidth tests so dropped connections are immediately recorded without hanging[cite: 1].
- **Automated Background Scheduler:** Uses APScheduler to run checks automatically every 10 minutes (adjustable from 1 minute to 1 hour directly from the UI, with Pause/Resume controls)[cite: 1].
- **Thread-Safe Execution:** Prevents overlapping manual and scheduled tests using thread locking (`threading.Lock`)[cite: 1].
- **Interactive Analytics Dashboard:** Real-time bandwidth timeline built with Chart.js featuring red outage markers, uptime percentage, peak speeds, and latency tracking[cite: 1].
- **One-Click CSV Export:** Download your complete ISP performance log (`wifi_speed_outage_report.csv`) to share with your broadband provider[cite: 1].

---

## Tech Stack

- **Backend:** Python 3, Flask 3.0.3, APScheduler 3.10.4, speedtest-cli 2.1.3[cite: 1]
- **Database:** SQLite3 (`data/wifi_logs.db`)[cite: 1]
- **Frontend:** HTML5, CSS3 (Glassmorphism Dark Mode), Vanilla JavaScript, Chart.js 4.4.3[cite: 1]

---

## Project Structure

```text
wifi-speed-outage-logger/
├── app.py                  # Flask web server, REST API & background scheduler[cite: 1]
├── monitor.py              # Connectivity checker & speedtest-cli wrapper[cite: 1]
├── database.py             # SQLite initialization, queries & sample data seeder[cite: 1]
├── requirements.txt        # Python dependencies[cite: 1]
├── README.md               # Setup & usage guide[cite: 1]
├── data/                   # Auto-created SQLite database directory (wifi_logs.db)[cite: 1]
├── templates/
│   └── index.html          # Main dashboard UI template[cite: 1]
└── static/
    ├── css/
    │   └── style.css       # Modern glassmorphism dark-mode styling[cite: 1]
    └── js/
        └── dashboard.js    # Interactive Chart.js graphs & live API polling[cite: 1]

INSTALL ON YOUR SYSTEM:-

git clone [https://github.com/your-username/wifi-speed-outage-logger.git](https://github.com/your-username/wifi-speed-outage-logger.git)
cd wifi-speed-outage-logger


STEP 1 :- python -m venv venv
STEP 2 :- pip install -r requirements.txt
STEP 3 :- python app.py

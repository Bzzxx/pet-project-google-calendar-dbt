# Google Calendar Analytics Pipeline (dbt + Snowflake + GitHub Actions)

A complete end-to-end analytics engineering project built with **dbt**, **Snowflake**, and **GitHub Actions**.  
The pipeline transforms raw Google Calendar event & attendee data into structured analytical marts
for reporting, automation, and trend analysis.

---

## 🌟 Project Overview

This project demonstrates a **production-ready data transformation workflow**, including:

- dbt for SQL modeling, testing & documentation  
- Snowflake as a cloud data warehouse  
- GitHub Actions for automated nightly builds  
- Google Calendar API as the raw data source  
- Multi-layer dbt architecture (staging → intermediate → marts)  

The pipeline extracts raw events & attendee metadata and turns them into insights such as:

- Daily & weekly event distributions  
- Number of attendees per event  
- Attendee status trends  
- Calendar usage patterns  
- Event-level analytical mart for reporting  

---

## 📊 Dataset

The project uses exported data from the **Google Calendar API**, loaded into Snowflake via external tools.

### **Source tables (raw → staging):**

#### `STG_EVENTS`
Contains event metadata such as title, start/end timestamps, description, event status, and calendar ID.

#### `STG_ATTENDEE`
Contains attendee-level data: email, status, organizer flag, optional flags, etc.

#### `STG_CALENDAR_LIST`
Contains metadata about user's calendars (name, color, visibility).

---

## 🧱 Project Structure (dbt)

```text
google_calendar_project/
│
├── models/
│   ├── staging/
│   │   ├── stg_events.sql
│   │   ├── stg_attendee.sql
│   │   └── stg_calendar_list.sql
│   │
│   ├── intermediate/
│   │   └── int_events_with_attendees.sql
│   │
│   ├── marts/
│   │   ├── attendees_status_summary.sql
│   │   ├── calendar_events_summary.sql
│   │   ├── events_daily_weekly_summary.sql
│   │   └── schema.yml
│   │
│   └── sources/
│       └── google_calendar_sources.yml
│
├── logs/
├── target/
└── README.md
```
---
🧪 Data Testing
<details> <summary><strong>💡 Click to expand</strong> — dbt tests used in this project</summary>
✔️ Built-in tests

not_null
unique
relationships
✔️ Custom logic
Ensuring event-attendee grain consistency
Status distribution validation
Event date completeness tests
📍 Test location

All mart-layer tests are stored in:
</details>

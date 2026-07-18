Task
HappyPaws has collected three datasets over the past year:

"pet_activities.csv" which logs daily activities of pets,
"pet_health.csv" which records vet visits and health issues, and
"users.csv" which contains information about the pet owners.
Each dataset contains unique identifiers for pets and/or their owners.

The engineers developing the app currently write code to cross reference all of these data sources.

They want to make things easier by having a single table with all data included.

Your manager has asked you to write a Python function that cleans and merges these datasets into a single dataset.

The final dataset should provide a comprehensive view of each pet's activities, health records, and owner information.

To test your code, your manager will run only the code all_pet_data('pet_activities.csv', 'pet_health.csv', 'users.csv')
Your all_pet_data() function must return a DataFrame, with columns as described below.
All columns must accurately match the descriptions provided below, including names.
Data
The data that has been provided has the following structure

<img width="509" height="337" alt="image" src="https://github.com/user-attachments/assets/6487ec13-2607-435e-b6da-61431b4d29ee" />


The function that you write must return data as described below. There should be a unique row for each activity/health visit.

Where missing values are permitted, they should be in the default Python format.

| Column | Description |
|---|---|
| `pet_id` | Unique pet identifier |
| `date` | Date of the activity or health visit |
| `activity_type` | `Walking`, `Playing`, `Resting`, or `Health` |
| `duration_minutes` | Duration in minutes (`0` for health rows) |
| `issue` | Health issue / check-up note (activity rows are blank) |
| `resolution` | Outcome or advice given (activity rows are blank) |
| `owner_id` | Unique owner identifier |
| `owner_age_group` | Owner's age bracket, e.g. `26-35` |
| `pet_type` | `Dog`, `Cat`, `Rabbit`, `Hamster`, `Fish` |


```text
HappyPaws_Project/
│
├── HappyPaws clinic.ipynb     # Data cleaning/merge + static Matplotlib/Seaborn dashboard
├── all_data                   # Final merged dataset (CSV, no extension)
├── app.py                     # Interactive Streamlit dashboard
├── requirements.txt           # Python dependencies
├── happypaws_dashboard.png    # Exported static dashboard image
└── README.md                  # This file
```


Analysis of HappyPaws Clinic's pet activity and health data, split across two notebooks:

1. **`HappyPaws DataCleaning.ipynb`** — cleans and merges the three raw source files
   into a single dataset (`all_data`).
2. **`HappyPaws Dashboard.ipynb`** — loads `all_data` and builds a static analytical
   dashboard with Matplotlib and Seaborn.

## Dataset

Three raw files come in:

- `pet_activities.csv` — daily pet activities (Walking, Playing, Resting) with duration
- `pet_health.csv` — vet visits, with an issue and resolution
- `users.csv` — owner information

`HappyPaws DataCleaning.ipynb` cleans and merges these into `all_data`, one row per
activity or health record:

| Column | Description |
|---|---|
| `pet_id` | Unique pet identifier |
| `date` | Date of the activity or health visit |
| `activity_type` | `Walking`, `Playing`, `Resting`, or `Health` |
| `duration_minutes` | Duration in minutes (`0` for health rows) |
| `issue` | Health issue / check-up note (blank for activity rows) |
| `resolution` | Outcome or advice given (blank for activity rows) |
| `owner_id` | Unique owner identifier |
| `owner_age_group` | Owner's age bracket, e.g. `26-35` |
| `pet_type` | `Dog`, `Cat`, `Rabbit`, `Hamster`, `Fish` |

Date range: **2022-04-01 → 2023-12-30**, covering 522 pets and 522 owners.

## Dashboard

`HappyPaws Dashboard.ipynb` builds a single 4×3 panel static dashboard
(`happypaws_dashboard.png`) straight from `all_data`, no intermediate summary tables:

- Records over time (monthly)
- Number of pets by pet type
- Activity vs. health record split
- Activity records by type, and average duration by activity/pet type
- Most common health issues, and health visits by pet type
- Owners by age group
- Activity-duration distribution
- Records by day of week
- Activity duration vs. health visits per pet (observed association only, not causation)
<img width="2985" height="3241" alt="happypaws_dashboard" src="https://github.com/user-attachments/assets/0a362160-32af-4c9c-97f3-84baba9246a7" />

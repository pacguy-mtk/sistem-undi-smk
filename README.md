# Sistem D'Undi Subjek Kegemaran

This folder contains the **single-file, pure frontend** voting system:

- [sistem_undi_pure_frontend.html](https://pacguy-mtk.github.io/sistem-undi-smk/))

The app is a compact voting demo for favorite school subjects. It runs entirely in the browser with **vanilla JavaScript**, **Tailwind CSS**, and **localStorage**. No backend, database, PHP, or server setup is required.

## Summary

The application supports two roles:

- **Student**
  - Register a new account
  - Log in with IC and password
  - View available subjects
  - Vote only once
  - See live results

- **Admin**
  - Log in with a fixed admin account
  - Add subjects
  - Delete subjects
  - View all students and vote status
  - Reset all votes
  - Export all data as JSON
  - Import JSON backup to replace existing data

The UI is intentionally compact:

- Login page: minimal, no long explanations
- Student view: card-based and slightly more engaging
- Admin view: spreadsheet-like, data-first, and table-oriented
- Results view: ranked list with simple visual bars

## File Included

### `sistem_undi_pure_frontend.html`

This is the complete app in one HTML file. It includes:

- Inline CSS
- Inline JavaScript
- Tailwind CSS CDN
- Google Font: Inter
- All views shown/hidden using JavaScript

## Core Features

### 1. Authentication

- Students can register with:
  - name
  - IC number
  - password
  - password confirmation
- Login mode can be switched between:
  - student
  - admin
- Session state is stored in `localStorage`

### 2. Student Voting

- A student can vote once only.
- After a vote is recorded:
  - the student is marked as voted
  - the vote button is disabled
  - a success screen shows the timestamp

### 3. Results

- Subjects are sorted by vote count in descending order.
- Results are shown in:
  - a ranked list
  - a simple bar-style display

### 4. Admin Management

- Add new subject
- Delete subject with confirmation
- Reset all votes with confirmation
- View student roster and vote status
- Export all application data as JSON
- Import JSON and replace current data

## Data Storage

All application data is stored under one `localStorage` key:

- `sistem_undi_data`

The current session is stored under:

- `sistem_undi_session`

## Data Structure

The stored data follows this shape:

```json
{
  "students": [
    {
      "id": 1,
      "name": "Ali",
      "ic": "010101010101",
      "password": "hash",
      "hasVoted": false
    }
  ],
  "subjects": [
    {
      "id": 1,
      "name": "Sains Komputer",
      "votes": 0
    }
  ],
  "votes": [
    {
      "studentId": 1,
      "subjectId": 2,
      "timestamp": "2026-06-21T10:30:00.000Z"
    }
  ],
  "admin": {
    "username": "admin",
    "password": "admin123"
  }
}
```

Notes:

- Passwords are stored using a lightweight demo hash approach in the browser.
- This is fine for a frontend demo, but it is not intended to be production security.

## Admin Account

Use these credentials to log in as admin:

- **Username:** `admin`
- **Password:** `admin123`

The admin password is intentionally not shown in the app UI, but it is documented here for testing and handoff.

## Export and Import

### Export JSON

- Click **Export JSON** in the admin dashboard.
- The browser downloads a backup file named:
  - `undi_data_backup.json`

### Import JSON

- Click **Import JSON** in the admin dashboard.
- Select a valid JSON backup file.
- The app validates the file and asks for confirmation.
- If confirmed, the imported data **replaces all current data**.

## Views in the Single HTML

- **Login**
  - Compact landing page
  - Role toggle for student/admin

- **Register**
  - Student registration form
  - Password confirmation

- **Student Dashboard**
  - Compact subject cards
  - Vote button
  - Vote status

- **Vote Success**
  - Confirmation message
  - Timestamp

- **Results**
  - Sorted ranking
  - Visual bars

- **Admin Dashboard**
  - Subject table
  - Student table
  - Add subject form
  - JSON import/export
  - Reset votes

## UI Notes

The visual style is split by mode:

- **Student mode**
  - darker, slightly more colorful
  - card-based layout
  - cleaner and more engaging

- **Admin mode**
  - light, spreadsheet-like appearance
  - compact rows
  - table-first layout
  - minimal explanation text

## How to Run

1. Open `sistem_undi_pure_frontend.html` in any modern browser.
2. If Tailwind CDN or Google Fonts are unavailable, the app still functions, but the styling will be reduced.
3. Register a student account or log in with the admin credentials above.

## Important Behavior

- Students can only vote once.
- Resetting votes clears:
  - all subject vote counts
  - all student vote flags
  - all recorded vote entries
- Importing JSON overwrites current data after confirmation.
- The app remains usable offline after the first load for the stored data, but the CDN assets may require internet on the first open.

## Suggested Test Flow

1. Log in as admin.
2. Add a few subjects.
3. Register a student.
4. Log in as the student.
5. Cast one vote.
6. Check results.
7. Export JSON.
8. Reset votes.
9. Import the exported JSON backup.

## Deliverable Location

- App: [outputs/sistem_undi_pure_frontend.html](./sistem_undi_pure_frontend.html)
- Report: [outputs/README.md](./README.md)


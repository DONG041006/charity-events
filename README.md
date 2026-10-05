# Charity Events Management System

**PROG2002 A2 - Web Development II**

A dynamic charity event management website built with **MySQL + Node.js + Express (backend API)** and **plain HTML/CSS/JS (frontend)**.

> Constraint: no CSS frameworks, no JS frameworks, no Express template engines (EJS/Pug etc.), no AngularJS.



***

## Features



* **Home page (index.html)**: displays all `upcoming` and `ongoing` charity events as cards (category, date, location, organization, ticket price). Click an event to view its details.

* **Search page (search.html)**: filter active events by date, location (fuzzy match) and category, individually or combined.

* **Event detail page (detail.html)**: shows the full event information, the organizing charity, and a fundraising progress bar. The Register button shows an "under construction" message.

## Project structure



```
charity-events/
├── server/                    # Backend
│   ├── event_db.js            # MySQL connection pool (mysql2)
│   ├── server.js              # Express server + REST API
│   ├── package.json
│   └── schema.sql             # Database schema + seed data
├── client/                    # Frontend (static files)
│   ├── index.html
│   ├── search.html
│   ├── detail.html
│   ├── css/style.css
│   └── js/{common,index,search,detail}.js
├── report/                    # Project report (.docx)
└── README.md
```

## Database design

Three tables:



| Table                   | Purpose                          |
| ----------------------- | -------------------------------- |
| `charity_organizations` | Charity organization information |
| `event_categories`      | Event categories                 |
| `charity_events`        | Charity events (core table)      |

Relationships: one organization can host many events (`organization_id` foreign key); one category can contain many events (`category_id` foreign key). Both use `ON DELETE CASCADE`.

## API endpoints



| Method | Path                                           | Description                                       |
| ------ | ---------------------------------------------- | ------------------------------------------------- |
| GET    | `/api/events/upcoming`                         | Homepage: upcoming + ongoing events               |
| GET    | `/api/categories`                              | All categories (search dropdown)                  |
| GET    | `/api/events/search?date=&location=&category=` | Filter events (optional params)                   |
| GET    | `/api/events/:id`                              | Full details of one event (includes organization) |

## Quick start



```
# 1. Create the database (start MySQL first)
mysql -u root -p < server/schema.sql

# 2. Install dependencies
cd server
npm install

# 3. Set your MySQL password
#    Open server/event_db.js and set the password field

# 4. Start the server
node server.js
# Expected output: "Database connected successfully!" and "Server running: http://localhost:3000"

# 5. Open in the browser
#    Home:   http://localhost:3000/
#    Search: http://localhost:3000/search.html
```

## Submission checklist



* Project report: `report/project-report.docx`

* Client code: zip the `client/` folder

* Server code: zip the `server/` folder (**excluding node\_modules**)

* GitHub repository: public, with multiple commits

* Demo video: max 15 minutes (API demo, data flow, website walkthrough)

* GenAI usage declaration and academic integrity statement

## Author

\[Sun_Xudong] - \[24832708]

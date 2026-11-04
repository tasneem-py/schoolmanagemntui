# School Management System (UI)

**Kamran MANUU Model School, Darbhanga, Bihar**
Academic Session: **2026-27**
Summer Internship Project

A responsive School Management System user interface built with React.js, JavaScript and Tailwind CSS. All data is dummy/local, so **no backend or database is required**.

---

## Technologies Used

| Technology | Purpose |
|---|---|
| React.js (Create React App) | Component based UI |
| JavaScript (ES6) | Application logic |
| Tailwind CSS v3 | Styling and responsive design |
| React Hooks (useState, useEffect) | State management |

No extra UI or chart library is used. Icons are inline SVG and the attendance chart is built with plain `div` elements, so every line of the project can be explained during the viva.

---

## Setup Instructions

You need **Node.js 16 or above** installed.

```bash
# 1. Go into the project folder
cd kamran-manuu-school-management-system

# 2. Install dependencies
npm install

# 3. Start the development server
npm start
```

The app opens at **http://localhost:3000**

To create a production build:

```bash
npm run build
```

### Demo Login

| Field | Value |
|---|---|
| Email | tasneem.qaisar@kmms.edu.in |
| Password | admin123 |

There is no backend, so any non-empty email and password will also log you in.

---

## Folder Structure

```
kamran-manuu-school-management-system/
├── package.json
├── tailwind.config.js
├── postcss.config.js
├── README.md
├── public/
│   └── index.html
└── src/
    ├── index.js                  # React entry point
    ├── index.css                 # Tailwind directives + reusable classes
    ├── App.js                    # Main component: state + page routing
    ├── data/                     # Dummy data files
    │   ├── schoolInfo.js
    │   ├── students.js
    │   ├── teachers.js
    │   ├── classes.js
    │   └── dashboardData.js
    ├── components/               # Reusable components
    │   ├── Sidebar.js
    │   ├── Navbar.js
    │   ├── StatCard.js
    │   ├── Badge.js
    │   ├── Modal.js
    │   ├── AttendanceChart.js
    │   ├── StudentFormModal.js
    │   ├── StudentDetailsModal.js
    │   └── Icons.js
    └── pages/                    # Screens
        ├── Login.js
        ├── Dashboard.js
        ├── Students.js
        ├── Teachers.js
        ├── Attendance.js
        └── Classes.js
```

---

## Pages and Features

### 1. Login
School logo and name, username/email field, password field, Remember Me checkbox, Forgot Password link and a Login button.

### 2. Dashboard
- Stat cards: Total Students, Total Teachers, Total Classes, Today's Attendance
- Present and Absent counters
- Weekly attendance bar chart
- Recent Activities list
- Upcoming Events list
- Quick Actions panel
- Logged-in user: **Tasneem Qaisar**

### 3. Students
Table with Student Name, Roll Number, Class, Section, Father's Name, Contact, Attendance %, Status and Actions. Supports live search, class filter, section filter, Add Student modal, Edit Student modal, View Details modal and Delete.

### 4. Teachers
Table with Teacher Name, Subject, Class, Email, Contact and Status. Includes **Nadeem Qaisar** (Principal, Mathematics).

### 5. Attendance
Class selector, section selector, date selector, student list with Present/Absent buttons, live attendance percentage with a progress bar and a Save Attendance button.

### 6. Classes
Classes 6 to 12 shown as cards and as a summary table with Section, Class Teacher, Subject, Room and Number of Students.

---

## Viva Notes (quick answers)

**Q. How does page navigation work without React Router?**
`App.js` keeps an `activePage` state variable. The `renderPage()` function uses a `switch` statement to return the matching page component. This is simpler than React Router and enough for a single-page admin panel.

**Q. Where is the data stored?**
In plain JavaScript files under `src/data/`. `App.js` loads the student list into `useState`, so Add, Edit and Delete update the UI immediately. Data resets on page refresh because there is no backend.

**Q. How is search and filtering implemented?**
With the JavaScript `Array.filter()` method on the students array, combined with `useState` for the search text and the selected class/section.

**Q. How is the app made responsive?**
Tailwind responsive prefixes (`sm:`, `lg:`). The sidebar is fixed and off-screen on mobile (`-translate-x-full`) and slides in when the hamburger menu is tapped; it is always visible on large screens (`lg:translate-x-0`).

**Q. How is the chart drawn?**
`AttendanceChart.js` maps over the weekly data and renders one `div` per day, setting its height from the percentage value. No chart library is needed.

**Q. How does one modal handle both Add and Edit?**
`StudentFormModal` receives a `student` prop. If it is `null` the form is empty (Add mode); if a student object is passed, `useEffect` fills the form (Edit mode).

---

## Future Scope

- Connect to a backend (Node.js + Express + MongoDB) so data is saved permanently
- Role based login for Admin, Teacher and Student
- Fee management, examination and report card modules
- Export attendance and student lists to PDF or Excel

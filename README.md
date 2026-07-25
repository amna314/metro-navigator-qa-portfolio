# Metro Navigator QA Portfolio

This portfolio shows the manual QA testing I did for an AI-powered metro bus navigation app built with Flutter, Flask and SQLite. It includes test cases, API testing, SQL testing, bug reports, Jira tracking and QA documentation completed during my Final Year Project.

## Architecture

```
Flutter Mobile App
        │
        ▼
Flask REST API
        │
        ▼
SQLite Database
```

## Testing Summary

- 15 Manual Test Cases
- 7 API Test Cases
- 10 SQL Test Queries
- 6 Bugs Reported
- 4 Bugs Fixed
- 2 Open Bugs

| Metric | Result |
|--------|--------|
| Test cases executed | 15 |
| Test cases passed | 10 |
| Test cases failed (initial run) | 5 |
| Bugs found | 6 |
| Bugs fixed | 4 |
| Open bugs | 2 |

The 2 open bugs are both in the login module: the Forgot Password feature does not send a reset email, and a technical error message shows up instead of a simple network error message.

**All failed test cases resulted in valid defects that were reported in Jira. Four defects were fixed and successfully retested, while two remain open.**

## Skills Demonstrated

- Manual Testing
- Test Case Design
- Test Execution
- Functional Testing
- Regression Testing
- Negative Testing
- Boundary Value Analysis (BVA)
- API Testing (Postman)
- SQL & Database Testing
- Bug Reporting (Jira)
- Retesting
- Git & GitHub

## Project Overview

Metro Navigator is an AI-powered metro bus navigation app built with Flutter, Flask and SQLite.

As the main QA tester for this Final Year Project, I was responsible for manual testing, API testing, SQL testing, bug reporting, regression testing and QA documentation.

**Testing approach:** I focused on negative and boundary testing more than simple UI checks, since the biggest risk in this app was in the route and fare calculation logic, not just the screens. Because of this, most of the bugs I found came from testing wrong or unusual inputs, not just normal use. I also tested the database directly using SQL to catch problems that would not show up just by using the app.

## Screenshots

All application screens, validation results, and Jira bug reports captured during testing are available in the [`screenshots/`](screenshots/) folder.

## Notable Bugs Found

### Fare not calculated during Red→Orange transfer

**Severity:** High
**Status:** Fixed

The app showed a blank fare when travelling between the Red Line and the Orange Line. After the fix, the correct transfer fare (Rs. 130) is shown.

### Same source/destination produced a strange route

**Severity:** High
**Status:** Fixed

When the same station was entered as both source and destination, the app created a route to a nearby station and then walked back, instead of recognizing they were the same. After the fix, the app shows a message saying the user is already at their destination.

### Route generated for a station outside the service area

**Severity:** High
**Status:** Fixed

Entering a station outside the service area (for example, Lahore) as the destination made the app show a route to a different, unrelated station instead of an error. After the fix, the app correctly shows an "outside service area" message.

### Route with no stations linked (found through SQL testing)

**Severity:** High
**Status:** Reported

Route RT04 (Green Line) existed in the database with all its details, but had no stations linked to it. Selecting this route in the app would show an empty route with no stops. This bug was found by checking the database directly, not from using the app.

*Full details for each bug, including steps to reproduce and retest results, are in `Bug_Reports.xlsx`.*

## Repository Contents

| File | Description |
|------|-------------|
| Login_Test_Cases.xlsx | Login module test cases |
| Route_Test_Cases.xlsx | Route search test cases |
| Bug_Reports.xlsx | Bugs reported during testing |
| QA_Summary_Report.xlsx | Overall testing summary |
| API_Test_Cases.xlsx | API testing |
| API_Testing_README.md | API testing approach and results |
| Metro_Bus_API_Test.postman_collection.json | Postman collection used for API testing |
| SQL_Testing_Results.xlsx | Database testing |
| SQL_Testing_README_Section.md | SQL testing approach and results |
| screenshots/ | Application screens, validation results, Jira bug reports |

## Testing Approach

Testing included functional, negative and boundary testing across the login and route search modules. API testing was performed using Postman against the Flask backend, while SQL queries were run directly on the SQLite database to check data correctness and relationships between tables. Bugs were logged in Jira, retested after fixes, and documented throughout the testing cycle.

## Tools & Technologies

**Testing**
- Jira
- Postman

**Development Stack**
- Flutter
- Flask
- SQLite

**Documentation**
- Microsoft Excel
- Git
- GitHub

## Test Environment

| Item | Detail |
|------|--------|
| Operating System | Windows 10 |
| Browser | Google Chrome |
| Frontend | Flutter |
| Backend | Flask |
| Database | SQLite |

## Contact

- GitHub: https://github.com/amna314
- LinkedIn: https://www.linkedin.com/in/amna-shaheen-11aa5a31b

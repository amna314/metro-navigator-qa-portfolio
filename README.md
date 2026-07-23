# Metro Navigator QA Portfolio

## About this project

Metro Navigator is an AI-powered metro bus navigation app built with Flutter, Flask and SQLite. This repository contains the manual QA testing I performed for my Final Year Project (FYP). I was responsible for manual testing, backend QA, database testing, writing test cases, reporting bugs in Jira, and retesting fixes after they were implemented.

## What is included

This repository contains the following files.

| File | Description |
|---|---|
| Login_Test_Cases.xlsx | 6 test cases for the login screen, covering valid login, wrong password, wrong email, empty fields and no internet connection |
| Route_Test_Cases.xlsx | 9 test cases for the route search feature, including normal routes, same source and destination, invalid stations and line transfers |
| Bug_Reports.xlsx | 6 bug reports found during testing, with steps to reproduce, expected and actual behaviour, severity and the retest result after each fix |
| QA_Summary_Report.xlsx | An overall summary of all testing, including pass rate and number of bugs found and fixed |
| API_Test_Cases.xlsx | 7 API test cases executed in Postman against the Flask backend, covering health check, stations, search and login endpoints |
| API_Testing_README.md | Details of the API testing approach and results |
| Metro_Bus_API_Test.postman_collection.json | Postman collection used for API testing |
| SQL_Testing_Results.xlsx | 10 SQL test queries executed against the metro.db database, covering data integrity, referential integrity and ordering checks |
| SQL_Testing_README_Section.md | Details of the SQL testing approach and results |

The `screenshots/` folder contains application screens, validation results, and Jira bug reports used during testing.

## Testing summary

A total of 15 test cases were executed across the login and route search modules. 5 test cases failed during the first execution due to real defects. These bugs were reported, fixed by my teammate, and verified through retesting.

| Metric | Result |
|---|---|
| Test cases executed | 15 |
| Test cases passed | 10 |
| Test cases failed (initial run) | 5 |
| Bugs found | 6 |
| Bugs fixed | 4 |
| Open bugs | 2 |

The 2 open bugs are both in the login module. One is the Forgot Password feature not sending a reset email, and the other is a technical error message showing instead of a simple network error message.

## Notable Bugs Found

**Bug 1: Fare not calculated for a line transfer**
Issue: The application showed a blank fare when travelling between the Red Line and the Orange Line.
Expected result: The application should calculate the transfer fare correctly.
After fix: The fare is now displayed correctly as Rs. 130.
Severity: High
Status: Closed

**Bug 2: Same source and destination created a strange route**
Issue: When the same station was entered as both the source and the destination, the app created a strange route that went to a nearby station and then walked back.
Expected result: The application should inform the user that they are already at their destination instead of generating a route.
After fix: The app now shows a simple message saying the user is already at their destination.
Severity: High
Status: Closed

**Bug 3: Route generated for a station outside the service area**
Issue: A station name that does not exist in the service area, such as Lahore, was entered as the destination, and the app generated a route to a different station instead of showing an error.
Expected result: The application should tell the user that the station is outside the metro service area (Islamabad/Rawalpindi only).
After fix: The app now correctly shows this message and no longer generates a route.
Severity: High
Status: Closed

**Bug 4: Route exists with no stations linked (found via SQL testing)**
Issue: Route RT04 (Green Line) existed in the routes table with full details (name, colour, start and end station) but had no stations linked to it in the route_stations table.
Expected result: Every route should have at least one station linked to it.
Actual result: Selecting this route in the app would show an empty route with no stops.
Severity: High
Status: Reported

## Testing Approach

Testing was done manually using functional and negative test techniques, including boundary and validation checks. Testing covered both positive and negative scenarios, including input validation, route calculation, fare calculation and error handling. In addition to manual UI testing, API testing was performed using Postman against the Flask backend, and SQL testing was performed directly against the metro.db database to check data integrity, referential integrity and correct ordering of stations within routes. Bugs were logged and tracked in Jira, and each fixed bug was retested before being marked as closed. This repository reflects the full testing cycle from writing test cases to finding bugs, tracking them and confirming the fix.

## Test Environment

| Item | Detail |
|---|---|
| Operating System | Windows 10 |
| Browser | Google Chrome |
| Frontend | Flutter |
| Backend | Flask |
| Database | SQLite |

## Skills Demonstrated

Manual Testing, Functional Testing, Negative Testing, Boundary Value Analysis, Bug Reporting, Regression Testing, Retesting, API Testing, Postman, SQL, Database Testing, Jira, Microsoft Excel

## About Me

I am a final-year Computer Science student at the International Islamic University Islamabad, with an interest in software quality assurance. This repository shows my practical experience in manual testing, bug reporting, retesting and QA documentation as part of my Final Year Project.

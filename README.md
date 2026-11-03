# student-club-tracker
A web-based application that allows a university to manage student clubs, members, events, and club activities.

# features
Dashboard - Overview of clubs, students, and events <br>
Club Management - Create, edit, delete, and view clubs <br>
Student Management - Register and manage students <br>
Membership - Add student to clubs <br>
Event Management - Create and manage club events <br>
Attendance - Track event participation <br>
Club Officers - Assign presidents, vice presidents, etc. <br>
Reports - Generate membership and event reports. <br>
Login System - Admin and authorized user access.

# designing the database
## tables
Students, Clubs, Events, FacultyAdvisors, ClubCategories, Memberships, EventAttendance, ClubOfficers

# the entity relationship diagram (ERD)
1 means "exactly one" <br>
0..* means "zero or more" <br>

 ┌─────────────────┐                              ┌─────────────────┐
 │ FacultyAdvisors │                              │ ClubCategories  │
 ├─────────────────┤                              ├─────────────────┤
 │ PK AdvisorId    │                              │ PK CategoryId   │
 └────────┬────────┘                              └────────┬────────┘
          │1                                               │1
          │               ┌───────────────────┐            │
          └───────────────┤       Clubs       ├────────────┘
                     0..* ├───────────────────┤ 0..*
                          │ PK ClubId         │
                          │ FK CategoryId     │
                          │ FK AdvisorId      │
                          └───┬───────────┬───┘
                             1│           │1
              ┌───────────────┘           └───────────┐
              │0..*                               0..*│
     ┌────────┴────────┐                    ┌────────┴────────┐
     │   Memberships   │                    │     Events      │
     ├─────────────────┤                    ├─────────────────┤
     │ PK MembershipId │                    │ PK EventId      │
     │ FK StudentId    │                    │ FK ClubId       │
     │ FK ClubId       │                    └────────┬────────┘
     └──┬───────────┬──┘                            1│
       1│           │0..*                            │
    0..*│           │                            0..*│
┌────────┴─────────┐ │                      ┌─────────┴─────────┐
│   ClubOfficers   │ │                      │  EventAttendance  │
├──────────────────┤ │                      ├───────────────────┤
│ PK ClubOfficerId │ │                      │ PK AttendanceId   │
│ FK MembershipId  │ │                      │ FK EventId        │
└──────────────────┘ │                      │ FK StudentId      │
                     │                      └─────────┬─────────┘
                     │   ┌─────────────────┐          │0..*
                     └───┤    Students     ├──────────┘
                        1├─────────────────┤1
                         │ PK StudentId    │
                         └─────────────────┘


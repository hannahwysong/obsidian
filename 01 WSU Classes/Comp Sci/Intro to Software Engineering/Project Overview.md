Class: [[Intro to Software Engineering]]
Date: 08-27-2025
Topics: #software #software-engineering #project 

## Project Overview:

In this project you will create a website for DegreeAdmin, where you can select two or more majors and/or minors. The system should generate a list of pre-requisite courses, faculty members who teach the class, when the class is offered and allow the student to figure out if they can complete the requirements by the time they graduate.
* * *
## Completion CheckList

- [ ] Team Presentation: final project presentation 
- [ ] Team Deliverable: software requirements 
- [ ] Team deliverable: software test plan
- [ ] Team deliverable: final software source
- [ ] Team deliverable: weekly project progress reports
- [ ] Team website: containing weekly team report, team member information, overview of your project, software requirement specification, and software test plan.
- [ ] Private git repository: you must demonstrate that your team has a private repository. DO NOT make your repository public. If you accidentally make it public, do not be alarmed if your code is taken by someone else. It is your responsibility to keep your code safe.
- [ ] Individual deliverable: weekly individual progress reports

*** 

### User Types 
#### Student 

- can add two or more majors (i.e dual major) and minors 
- can create semester and year long schedules
- can request semester long co-ops for approval
- can view required courses for chosen majors and minors
- can evaluate whether they can finish a degree in a specified number of years given their chosen number of majors and/or minors and co-op selections

#### Faculty

- can approve addition of majors and minors
- an provide amendments to semester and year long schedules
- can change required courses for chosen majors and minors
- can provide guidance to students on whether they can complete a degree in a specified number of years given their chosen number of majors and/or minors and co-op selections

#### System Admin 

- can assign students to faculty
- can remove students from faculty
- an remove faculty accounts
- can update usernames and passwords

* * *

### Authentication 

- All users should be authenticated with a username and password
- All usernames must be 8-characters long, with only lowercase characters being allowed
- All passwords must be 12 characters long, with at least 1 uppercase, 1 lowercase, 1 numeric, and 1 symbol
- Username and passwords do not need to be hashed

---
### Interface 

- Students, faculty, and system administrators should be provided a single user interfaces
- Interactions after logging in will depend on the type of user, in other words you will need post log in interfaces for students, faculty, and system administrators


---
### Major and Minor 

- A minimum of 2 majors must be selected
- A minimum of 2 minors must be selected
- You will need to use the Wright State catalog to figure out what courses and prerequisites are needed for each major and minor. You will also need to figure out course offering information

---

## Number of Users

- [ ] Student 1: 1 major
- [ ] Student 2: 1 major and 1 minor
- [ ] Student 3: 1 major and 2 minors
- [ ] Student 4: 2 majors and 1 minor
- [ ] Student 5: 2 majors and 2 minors
- [ ] Faculty 1: advises 3 students
- [ ] Faculty 2: advises 2 students
- [ ] A minimum of 5 students must be created
- [ ] A minimum of 3 faculty must be created
- [ ] A minimum of 2 system administrators must be created




# Team Project CAP 2022
## POS APP FE AND BE General WorkFlow
POS Project (User):
- ✨Mas Purna ✨

## Features

- multi-tenant
- Stock Management
- Order
- Payment

## Tech

Team Project CAP 2022 (POS) use:

- [React JS] - HTML, CSS JS for react (must functional component for saving time). Tailwind or bootstrap for styling every component. Need Redux for state management.
- [Go gin gonic and gorm] - for saving time
- [Hexagonal Arch and monolith repo in BE] - Hexagonal Arch for saving time and use postgre and dbeaver when development
- [API contract] - must be clear both FE and BE
- [POSTMAN] - BOTH BE AND FE MUST TESTING ENDPOINT USING POSTMAN
- [Repo in FE React use vite for fastest rendering] - we don't use CRA anymore, please!!

## Installation

POS CAP 2022 requires version: go >= 1.17, node for react >= 12

## Project Management

Project CAP use jira for project and collaborate. Backlog will define for each member. 

| Tools | Free link |
| ------ | ------ |
| JIRA | [https://www.atlassian.com/software/jira/pricing][PlDb] |
| SLACK | [slack.com][PlGh] |

## Development

General workflow when development: 
1. Mempelajari requirement dari PRD/dokumen terkait (tanya ke mas purna)
2. Analisis entitas requirement (menggunakan user story dan ERD)
3. Kolaborasi FE DAN BE untuk membuat kontrak API
4. Breakdown task (listing task yang akan dikerjakan dan menentukan berapa bobot setiap tasknya)
5. Eksekusi setiap task (backlog)
6. Git clone di setiap repo (BE dan FE reponya akan terpisah) TBD.
7. Pastikan ketika mengerjakan setiap tasknya, buat branch masing-masing dulu kemudian git pull origin terlebih dahulu dari staging, ketika task udah selesai push ke branch masing-masing PR(pull request) ke branch staging. Deployment ke master di hari selasa atau kamis. Jika ada bug di main, langsung hotfix dengan cara PR(pull request) ke staging di hari rabu atau jumat, dari staging akan naik ke main. Deployment seminggu sekali minimal.
8. Kenapa ada staging? Jaga-jaga kalau main error bisa pull dari staging atau sebaliknya.
9. Daily kanban mau di jam berapa? daily kanban/scrum/daily meeting adalah update progress masing-masing SE (software engineer).
10. MARI KITA KODING (DENGAN NADA SISCA KOHL).

### react

```sh
npm create vite@latest
```

### golang
```sh
go mod init pos
```

## License

Team 3 CAP 2022

## What's next?
### TODO:
1. Initialize first commit on golang repo and react repo (8 am to 11 am) don't forget to install package on each repo.
2. SE must clone and pull each repo (both BE AND FE)
3. Gather Requirement from Mas Purna (after lunch)
4. After gather requirement, define user story and ERD on monday. 

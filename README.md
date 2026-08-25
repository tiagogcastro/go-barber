# go-barber

![React](https://img.shields.io/badge/React-17-61DAFB?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-4.x-3178C6?logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-14+-339933?logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-4-000000?logo=express&logoColor=white)
![TypeORM](https://img.shields.io/badge/TypeORM-0.2-FE0803?logo=typeorm&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)

GoBarber is a barbershop scheduling platform: customers book appointments with
their favorite barbers and providers manage their daily schedule. This
monorepo contains the web client and the REST API, built during the
[Rocketseat GoStack](https://rocketseat.com.br) bootcamp.

## Apps

| App | Path | Description |
|---|---|---|
| Web client | `apps/frontend` | React SPA for sign in, sign up, appointment booking and provider dashboard |
| API | `apps/backend` | Node/TypeScript REST API with JWT auth, appointments, uploads and notifications |

## Features

- Authentication with JWT (sign up, sign in, password recovery by email with Handlebars templates)
- Appointment booking with calendar picker and available time slot validation
- Provider dashboard to list appointments per day and month
- Profile management with avatar upload to AWS S3
- Notifications stored in MongoDB
- Rate limiting on auth routes backed by Redis
- Modular DDD-style backend structure with dependency injection (tsyringe) and Jest unit tests

## Tech stack

| Layer | Tools |
|---|---|
| Frontend | React 17, TypeScript, Create React App, styled-components, Unform, Yup, react-day-picker, axios |
| Backend | Node.js, Express, TypeScript, TypeORM, PostgreSQL, MongoDB, Redis, AWS S3, Nodemailer |
| Testing | Jest + ts-jest |

## How to run

### Requirements

Node.js 14-16 era runtime (see legacy note), plus running instances of PostgreSQL, MongoDB and Redis (docker-compose works well).

### Backend

```bash
cd apps/backend
yarn install
cp .env.example .env        # fill in database, Redis, Mongo and S3 credentials
yarn typeorm migration:run
yarn dev:server             # http://localhost:3333
```

### Frontend

```bash
cd apps/frontend
yarn install
yarn start                  # http://localhost:3000, expects API on port 3333
```

## Legacy note

Educational project built during the Rocketseat GoStack bootcamp (2020-2021).
Dependencies are pinned to that era: React 17 with Create React App 4,
TypeScript 4.1, TypeORM 0.2, Express 4. Expect friction on current Node
versions without upgrades. Estimated modernization effort if picked up later:
medium (1-2 days), migrating CRA to Vite, bumping all dependencies to current
majors and updating TypeORM config. No fixes are planned as part of this
cleanup phase.

## License

[MIT](LICENSE)

## Author

Built by [Tiago Gonçalves de Castro](https://github.com/tiagogcastro)
· [LinkedIn](https://www.linkedin.com/in/tiagogcastro)

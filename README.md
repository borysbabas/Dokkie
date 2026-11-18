# Dokkie

![Dokkie](wwwroot/assets/images/Dokkie_Logo.png)

A group payment site in the spirit of Tikkie: make an account, add an outing ("uitje"), and keep track of who joined
and who paid what. My first project at the HvA, from the first block of the propaedeutic year (2023–2024), built with
plain HTML, CSS and TypeScript on top of the HBO-ICT Cloud database.

## Stack

| | |
|---|---|
| Pages | Plain HTML and CSS, one file per page in `wwwroot/` |
| Scripts | TypeScript, one module per page, bundled by Vite |
| Data | MySQL on HBO-ICT Cloud, queried through `@hboictcloud/api` |

## Getting started

```bash
npm install
npm run dev     # http://localhost:3000
```

```bash
npm run build   # -> dist/
```

Database credentials go in `.env` and `.env.production` (see `src/hboictcloud-config.ts`); the schema is in
`dokkie_database.sql`. `@hboictcloud/api` comes from the HBO-ICT Cloud registry, which only works with a student
account.

## Database

| Table | |
|---|---|
| `User` | Accounts for signing in |
| `Event` | The outings |
| `Participant` | Who takes part in which outing |
| `Payment` | What each participant paid, when and what for |

The diagram is in [database_design.png](database_design.png).

## Project structure

| Path | |
|---|---|
| `wwwroot/index.html` | Home page |
| `wwwroot/registreren.html` | Sign up and sign in |
| `wwwroot/uitjes.html`, `wwwroot/uitjes_toevoegen.html` | The list of outings, and adding one |
| `wwwroot/faq.html`, `wwwroot/contact.html` | FAQ and contact |
| `wwwroot/assets/` | Styles, fonts, the logo and images |
| `src/login.ts`, `src/registratie.ts`, `src/check-login.ts` | Signing in, signing up, and sending signed-out visitors to the login page |
| `src/uitjes.ts`, `src/uitje_toevoegen.ts` | Reading and adding outings |
| `src/hboictcloud-config.ts` | Connects the pages to the HBO-ICT Cloud database |
| `docs/` | The original assignment readme, technical documentation and my reflection |

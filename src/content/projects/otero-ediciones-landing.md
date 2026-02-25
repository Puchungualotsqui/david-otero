---
title: Otero Ediciones Landing Page
description: >-
  This is the Angular frontend for the Otero Ediciones landing page.
  It displays a dynamic book catalog and a brief history of the editorial.
image: '@assets/projects/otero-ediciones-landing/image.png'
startDate: 2025-05-20
endDate: 2025-07-29
skills:
  - Angular
  - HTML
  - CSS
  - Go
  - Backend
  - Frontend
demoLink: https://oteroediciones.com/
sourceLink: https://github.com/Puchungualotsqui/otero_ediciones-landing_page
---
## Available Routes

| Route                        | Component            | Description                                 |
|-----------------------------|----------------------|---------------------------------------------|
| `/`                         | `HomeComponent`      | Landing page with featured books            |
| `/catalogo`                 | `CatalogoComponent`  | Full book catalog with filters              |
| `/catalogo/:simplified_name`| `BookDetailComponent`| Individual book detail page                 |
| `/historia`                 | `HistoriaComponent`  | About us / company history section          |

## 📦 Project Structure Highlights
```
src/
├── app/
│ ├── catalogo/
│ ├── home/
│ ├── historia/
│ ├── book-detail/
│ └── ...
├── assets/
├── index.html
└── main.ts
```

## 🖼️ Features

- Responsive layout
- Home expositor with categorized rows
- Filterable catalog (level, subject, type, language, search)
- Dedicated book detail view
- Static 'Historia' page with editorial background

## Backend available in
https://github.com/Puchungualotsqui/otero_ediciones-backend

# Finance Dashboard

A small, interactive finance dashboard built for a frontend assignment: summary metrics, charts, filterable transactions, role-based UI, and insights — all with mock/local data and no backend.

## Setup

Requirements: Node.js 18+ recommended.

```bash
cd finance-dashboard
npm install
npm run dev
```

Open the URL Vite prints (usually `http://localhost:5173`).

```bash
npm run build   # production build
npm run preview # serve build locally
```

## Approach

- **Stack:** React 18, TypeScript, Vite, Tailwind CSS, Recharts.
- **State:** One `FinanceProvider` (React Context) holds transactions, filters, role, and theme. Transactions persist to `localStorage`; role and theme preferences are stored separately.
- **Data:** Seed transactions in `src/data/mockData.ts`. You can edit data in the UI as **Admin**; changes persist in the browser.

## Features (assignment mapping)

| Requirement | Implementation |
|-------------|------------------|
| Summary cards | Total balance, income, expenses (`SummaryCards.tsx`) |
| Time-based chart | Monthly net balance area chart (`ChartsSection.tsx`) |
| Category chart | Expense breakdown pie + legend |
| Transactions | Table with date, description, category, type, amount |
| Filter / sort / search | Category, type, search box, sort by date/amount/category |
| Role-based UI | Header dropdown: **Viewer** (read-only) vs **Admin** (add/edit/delete, export) |
| Insights | Highest category, month-over-month spending, quick stats (`InsightsPanel.tsx`) |
| Empty states | No data / no filter matches handled in UI |
| Responsiveness | Responsive grid, scrollable table, stacked header on small screens |

## Optional extras included

- Dark mode (toggle + `class` on `document.documentElement`, preference saved).
- Persistence via `localStorage` for transactions, role, and theme.
- Export CSV and JSON (Admin only).

## Project structure

- `src/context/FinanceContext.tsx` — state, persistence, derived filtered list, export helpers, chart aggregations.
- `src/components/` — layout sections and the transaction modal.
- `src/types.ts` — shared TypeScript types.

## Notes

- Currency is formatted as USD via `Intl.NumberFormat`.
- “Balance trend” uses **monthly net** (income − expenses), not a running daily ledger balance.

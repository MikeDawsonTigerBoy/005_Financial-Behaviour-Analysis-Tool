# 005 Financial Behaviour Analysis Tool

A personal finance dashboard that shows spending behaviour over time, so patterns are visible and can be changed.

> **Draft for review.** This draft assumes it continues Mike's earlier MD100 (LifeLedger) work, which **Mike needs to confirm**. Lines tagged *(proposed)* are Claude's suggestions. Section 10 lists the questions to settle before building.

## Status

An earlier version, MD100, exists outside this repo. It's a self-contained HTML dashboard with a timeline view in the style of Ableton, drag-and-drop CSV/XLSX import, an Excel template, and a Python launcher that runs it locally. This repo is empty so far.

## 1. Problem statement

Bank apps show transactions, not behaviour. It's hard to see how spending moves over months, what drives it, and which habits are worth changing. Spreadsheets take too long to keep up.

## 2. Target audience

- **Primary:** Mike.
- **Secondary** *(proposed)*: people with financial independence goals who already export their bank statements.

## 3. Value proposition

Drop in your statements and see your money as a timeline of behaviour. Patterns show up without manual categorising.

## 4. Core functionality

- Import CSV or XLSX bank exports.
- Categorise transactions automatically, with corrections.
- A timeline view that zooms from day to year.
- Pattern views, such as recurring costs, spending creep and seasonal spikes *(proposed)*.
- Everything stays on your own device.

## 5. Key user journeys

1. **Monthly review:** import the month's statement, look at the timeline and spot one change worth making.
2. **Investigate:** select a spike on the timeline to see the transactions behind it.

## 6. Non-goals

*(proposed)*
- No bank connections or open-banking APIs in v1.
- No investment advice.
- No sharing or multiple users.

## 7. Feasibility

- MD100 proves the core works.
- The effort sits in turning messy bank exports into consistent data and categorising it well.

## 8. Assumptions and risks

- **Privacy:** financial data must never leave the device without explicit consent.
- **Insight isn't action:** charts on their own rarely change behaviour.

## 9. Success metrics

*(proposed)*
- Used every month for 6 months.
- One habit change a quarter that can be traced to an insight from the tool.

## 10. Open questions and challenges

1. **Mike to confirm:** is this MD100 continued, or a new tool?
2. **What does "behaviour analysis" mean exactly?** Is it describing what happened, explaining why, or nudging what happens next? These are three different products.
3. **What makes it different?** YNAB, Monarch and many spreadsheet templates exist. Is the edge the timeline view, keeping data on the device, or a goal like financial independence?
4. **Product or personal tool?** Is it meant to be a product for others, or a showcase of data and UX thinking? That decides how much to build.

## 11. Tech approach

Plain React web app, as decided for the portfolio, since it's a dashboard. Data stays in the browser or on the device.

## 12. Roadmap

- **v0 (done):** MD100 HTML dashboard.
- **v1:** React rebuild with import, categorising and the timeline.
- **Later:** pattern detection.

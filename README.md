# 005 Financial Behaviour Analysis Tool

A personal finance dashboard that shows spending behaviour over time, so patterns are visible and can be changed. It's a simpler, safer rebuild of MD100 (LifeLedger).

> **Draft for review.** Lines tagged *(proposed)* are Claude's suggestions, not yet agreed. Section 10 lists the questions to settle before building.

## Status

- **Focus: parked.** Not one of the featured prototypes for now.
- **Origin:** MD100 (LifeLedger), a self-contained HTML dashboard built in Claude chat. It has a timeline view in the style of Ableton, drag-and-drop CSV/XLSX import, an Excel template, and a Python launcher that runs it locally.
- **Plan:** rebuild it in Claude Code, simpler and with security guardrails.
- **Code:** the original MD100 code isn't in this repo yet. Mike to add it, or attach it when the rebuild starts.

## 1. Problem statement

Bank apps show transactions, not behaviour. It's hard to see how spending moves over months, what drives it, and which habits are worth changing. Spreadsheets take too long to keep up.

## 2. Target audience

- **Primary:** Mike.
- **Secondary** *(proposed)*: people with financial independence goals who already track figures in a spreadsheet.

## 3. Value proposition

Your own figures, shown as a timeline of behaviour. Everything stays on your device.

## 4. Core functionality

- Import a one-dimensional Excel sheet or CSV of figures, entered by hand.
- Categories and a timeline view that zooms from day to year.
- Pattern views, such as recurring costs, spending creep and seasonal spikes *(proposed)*.
- All data stays on the device.

## 5. Key user journeys

1. **Monthly review:** update the Excel sheet, drop it in, look at the timeline and spot one change worth making.
2. **Investigate:** select a spike on the timeline to see the entries behind it.

## 6. Non-goals

- No bank connections, open-banking APIs, account numbers or logins, ever.
- No investment advice.
- No sharing, multiple users or cloud sync in v1.

## 7. Feasibility

MD100 proves the core works. The rebuild is about simplifying it and putting in the security guardrails below.

## 8. Assumptions and risks

### Security and privacy guardrails

Mike's rule: data is entered by hand into a one-dimensional Excel sheet, and no account details or logins ever go to Claude, an MCP server or anyone else. That removes the biggest risk, which is someone getting into your bank accounts. Figures on their own still matter, though, so here is what to consider. This is good practice for fintech too.

- **Figures alone are still sensitive.** Income, balances, debts and spending show your lifestyle, where you go (from merchant names), and how wealthy you are. A leak won't empty your account, but it could enable scams, social engineering or embarrassment. Treat the sheet as private.
- **These repos are public.**
  - Never commit real figures. The repo holds code plus fake sample data only.
  - `.gitignore` blocks `.xlsx` and `.csv` files, except anything inside `samples/`.
- **Build with fake data.**
  - When working with Claude Code or Claude chat, use the sample sheet, not your real one.
  - Real figures pasted into a chat are sent to Anthropic. That's allowed, but it's a choice you don't need to make.
- **Keep the data on the device.**
  - The app reads the file in the browser.
  - No server, no analytics and no third-party scripts that could send data anywhere.
- **Keep only what you need.** Store amounts, dates and categories. Leave out reference numbers, account fragments and names of other people.
- **Encrypt saved data** *(proposed)*: optionally protect any saved state or export with a passphrase (WebCrypto in the browser).
- **Fintech practice, in brief:**
  - Know what data you hold and how sensitive each piece is.
  - Think through who could get at it and how.
  - Design privacy in from the start.
  - Keep in mind South Africa's POPIA and the EU's GDPR for anything that ever holds other people's data.

### Other risks

- **Insight isn't action:** charts on their own rarely change behaviour.

## 9. Success metrics

*(proposed)*
- Used every month for 6 months.
- One habit change a quarter that can be traced to an insight from the tool.
- No real data in the repo history, ever.

## 10. Open questions and challenges

1. **What does "behaviour analysis" mean exactly?** Is it describing what happened, explaining why, or nudging what happens next? These are three different products.
2. **What makes it different?** YNAB, Monarch and many spreadsheet templates exist. Is the edge the timeline view, keeping data on the device, or a goal like financial independence?
3. **What gets simplified?** Which parts of MD100 stay, and which go?

## 11. Tech approach

- Plain React web app, as decided for the portfolio, since it's a dashboard.
- Reads the file in the browser. No backend.

## 12. Roadmap

- **v0 (done):** MD100 HTML dashboard.
- **v1:** a simplified rebuild in React with the guardrails above.
- **Later:** pattern detection.

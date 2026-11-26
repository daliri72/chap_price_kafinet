# Codex instructions — کافی نت آینده

## Project
A Persian RTL, light-themed, client-side tariff search and invoice app for a copy/print shop. Current entry point: `index.html` (self-contained HTML/CSS/JS, with an embedded base64 source tariff image). Deploys on GitHub Pages. Do not add backend requirements for basic operation.

## Preserve (existing functionality)
- Persian RTL interface, light theme and compact animated developer credit on screen (محمد دلیری — کافی نت آینده — 09373317773).
- Fast live tariff search, category filters, Persian/Arabic character normalization; query «کپی»/«فتوکپی» must find «زیراکس سیاه و سفید» rates.
- Tariff prices transcribed from the provided 1405 image; treat image as the pricing source, not another business's price list. Do not arbitrarily alter rates or infer missing prices.
- Add services to invoice, modify quantity, add a custom line, discount and extra charges, customer name/phone, invoice number and date, print A4 invoice.
- Scrollable invoice list on screen, but ALL invoice rows must print; no clipped/scroll-only printed output.
- On invoice paper hide the large shop header and designer footer (existing `.print-heading,.print-footer` styles); preserve customer details, line items, totals and signatures unless explicitly requested otherwise.
- Works without network after downloaded; no external fonts or CDN dependencies; keep GitHub Pages deployment working.

## Important boundaries
- Currently NO database, login, cloud sync, reliable sales ledger, or automatic invoice persistence. Do not claim these exist.
- localStorage is local to one browser/device and can be erased. If implementing it, explain limits and add JSON export/import backup and safeguards.
- Browser-added print headers/footers (URL/date/page number) cannot be reliably disabled by HTML; user may need to turn off 'Headers and footers' in Chrome/Edge print dialog.
- Tariff unit semantics vary by service. Keep page vs sheet vs side distinctions explicit. Verify assumptions instead of silently changing pricing logic.
- Do not collect or publish real customers' data in the public GitHub repository.

## How to work
1. Inspect `index.html` and document current behaviors before editing.
2. Make incremental, testable changes. Prefer no-build plain HTML/CSS/JS modules if refactoring; maintain `index.html` at repo root.
3. Keep RTL/layout, mobile responsiveness, keyboard accessibility, search and print working.
4. Test: «کپی» finds Xerox BW; 20 items scroll on screen but all print; invoice totals with discounts/extra; empty-cart validation; invoice print has no app header/footer; mobile viewport; no console errors.
5. Never change tariff amounts without source confirmation. Preserve existing user data when changing persistence format.

## Suggested next milestone (not yet implemented)
- Local save/history of invoices, editing and reprinting saved invoices, export/import JSON backup, per-line manual price override.
- Separate pricing data from UI; add controlled price editing with confirmation, storing tariff snapshot on each invoice so old invoices remain unchanged.
- Detailed print calculator and payment status, then reporting. Scope and test each milestone independently.

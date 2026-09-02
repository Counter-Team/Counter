Carbon Border Counter — Rulebook (UK)

This file is the single source of truth for every official rule, threshold, date, test, source, dataset, number, and definition behind the Carbon Border Counter, plus every decision we made about how our app is allowed to use them.

Scope of this rulebook: the app is UK-only. This file covers the UK CBAM scheme only. Where a UK number is not published yet (the carbon price and the emission values), we use the equivalent EU number as a temporary stand-in until the UK releases its own — this is stated plainly wherever it applies, and those are the only places the EU is mentioned.

V1 build decisions (2026-09-01): currency conversion is in v1. Parked to October: the 30-day forward test, the frozen monthly record, the invoice↔declaration cross-check, and any £ tax figure (v1 shows CO₂ tonnes only). Details sit in each section and under “Parked items”.

What the app is (one line): a counter — it keeps a running total of a business's imports, works out which goods fall under the UK carbon-tax scheme, and warns the business before it crosses the threshold, so it doesn't find out too late and owe a whole year of charges.

Plain-English terms used throughout:

CBAM = Carbon Border Adjustment Mechanism — the official name for the "carbon tollbooth": a fee charged at the border for the pollution made when imported goods were manufactured.
De minimis threshold = the "small buyer" escape door: if you import below a set amount, you do nothing.
Counter = our tool: it counts value (and weight, for the tax estimate) and warns; it does not calculate final tax as the number to pay.
Calculator = the harder tool (which we are not building first): works out how much tax is owed, which needs real factory emissions data.
HMRC = His Majesty's Revenue and Customs, the UK tax office.
The UK scheme in one line
The source
The UK CBAM puts a carbon price on emissions-heavy goods imported into the UK, starting 1 January 2027.
It covers five sectors: aluminium, cement, fertiliser, hydrogen, iron & steel. It does not cover electricity. Glass and ceramics were dropped before launch.
It is a direct tax the importer self-assesses on an HMRC return — not a tradable-certificate system, and not a border tariff (it's worked out and paid after import, on a periodic return).
How we use it
The app keeps one running total per business, in £, against the UK £50,000 threshold.
The app decides, per business, whether the UK scheme applies to them before counting.
Thresholds and the two tests
The source
Registration threshold: £50,000 of in-scope goods over a rolling 12 months (measured in value, not weight). Raised from a proposed £10,000 to a final £50,000.
Rolling 12 months = always "the 12 months ending today," not a calendar year — the window slides forward each month.
There are two tests to decide if you must register:
Look-forward: you must register if you expect to import £50,000+ of CBAM goods within the next 30 days (from 1 January 2027).
Look-back: from 1 January 2027, on the first day of each month, check whether you imported £50,000+ of CBAM goods in the previous 12 months.
Don't count goods imported before 1 January 2027. If both tests apply, use the earliest date you became liable as your registration start date.
Below the threshold, you do nothing — no registration, no return, no report.
The £50,000 test is an administrative de minimis (deciding who joins the system), not a financial exemption below which the charge does not apply once you are over.
Private individuals importing for non-commercial purposes are not liable. UK-produced precursor goods re-imported inside a complex good can be deducted. (A precursor = a material used to make a bigger product, e.g. steel that goes into a machine.)

Numbers we count with:

Threshold: £50,000, in-scope goods value, rolling 12 months, from 1 Jan 2027.
https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
Look-forward window: 30 days, expected imports, from 1 Jan 2027.
https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
Look-back window: 12 months rolling, re-tested on the 1st of each month, from 1 Jan 2027.
https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
How we use it
The app's core job: keep the rolling 12-month running total of in-scope £ value, re-tested as of the 1st of each month, The separate 30-day forward check (which needs the business to enter expected imports, not just past ones) is not built in v1 — parked to October (decision 2026-09-01).
The app warns before the line, not after: an email at ~70% of the threshold, a louder one at ~90%, with a plain list of what happens next and by when.
The app tells the business the estimated crossing date based on how fast the total is climbing.
The app never says "you are compliant" — it only shows what the paperwork says and how close the total is to the line.
The 2027 / 2028 registration gap (most important point)
The source
Liability/counting starts 1 January 2027 — you must start adding up toward £50,000 and can become liable.
Registration opens by 1 January 2028 — you cannot register with HMRC before then.
If you become liable before registration opens, you must keep records of all CBAM goods you imported so you can register when the service is available.
(Verified directly on gov.uk on 2026-09-01: no contradiction — pre-2027 goods are excluded from the threshold, liability runs from 1 January 2027, and registration opens from 1 January 2028; HMRC’s own comms say “register from 1 January 2028, with their first return and payment due by 31 May 2028”.)

Dates we count with:

Liability start: 1 January 2027.
https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
Registration opens: by 1 January 2028.
https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
First-year registration deadline for those liable in year one: 31 January 2028 — <TO CONFIRM>: this exact date does not appear in the gov.uk guidance checked on 2026-09-01 (HMRC comms say only “register from 1 January 2028”, first return and payment by 31 May 2028). Confirm on gov.uk or drop.
How we use it
This gap is the strongest reason a small importer needs the app: during 2027 they are liable but cannot register, so their own records are the only proof they have.
The app's dated monthly record (see below) is therefore a core feature for 2027, not a nice-to-have — build it early, not last.
How you report and pay
The source
The UK CBAM is a direct tax you self-assess on an HMRC return, paid to HMRC. It is its own separate charge, not rolled into income tax, corporation tax, or VAT.
Reporting rhythm:
Year one (2027): one long annual accounting period (1 Jan–31 Dec 2027), with the return and payment due by 31 May 2028.
From 2028: accounting periods become calendar quarters, with returns and payments due on the last working day of the second month after each quarter ends.
Nil returns are required once registered — you must file even if you owe nothing, unless you de-register. (This does not apply to a business below the threshold that never registered.)
Legal liability sits with the importer named on the customs declaration — not the freight agent or broker (Finance Act 2026, section 146). A tax agent may submit CBAM returns on the importer's behalf, cannot register, and bears no legal liability. (The agent can still bear contractual risk to their client if they file badly.)
Carbon Price Relief (CPR): if you already paid a carbon price in the country where the goods were made, you can knock that off your UK bill.
Once you file a UK return using default values, you cannot amend it later to swap in real data.

Dates we count with:

UK year-one return + payment due: 31 May 2028 (for 2027 imports).
https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
Ongoing (from 2028): last working day of the 2nd month after each calendar quarter — <TO CONFIRM> exact page reference.
How we use it
The app is a counter, not a filer — it never files anything on anyone's behalf. Registering is a legal act with the importer's name on it.
The app can point a business to a straight "are you caught?" answer so the agent doesn't have to take on carbon advice.
The "can't amend after filing with defaults" point means any tax estimate the app shows must be clearly labelled "for planning only" (see tax section).
Commodity codes and scope (the field everything hinges on)
The source
A commodity code is the numeric ID that says exactly what a good is (8 digits is the key length). It decides whether a good is in CBAM scope.
A good is only in UK CBAM scope if its specific commodity code is on the official list — being in one of the five sectors is not enough.
The UK in-scope list is called Annex B ("Commodity codes within the scope of CBAM"), linked from the gov.uk "check which goods are in scope" page.
In-scope goods reach further than raw metal — they include screws, bolts and fasteners, aluminium doors and structures, nitric acid and ammonia.
Scrap is excluded — but only genuine scrap under the specific excluded codes; calling something "scrap" doesn't make it excluded, the code decides.
The government will keep the list under review and may update it.

Links:

https://www.gov.uk/government/publications/check-which-goods-are-in-scope-of-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
Commodity-code lookup tool: https://www.gov.uk/trade-tariff — checked on: 2026-09-01
How we use it
The app keeps its own scope list (a copy of Annex B) as a reference table, with a "date checked" column, because the list changes.
For each goods-line, the app matches the 8-digit code against the scope list and marks it in / out / borderline.
Hard line: the app can show the code on the paperwork and flag borderline codes, but must never decide a disputed code — that is a customs judgement. It flags for a human; it does not settle.
The customs declaration (structure of the data)
The source
CDS = Customs Declaration Service — HMRC's online system (not a document). Agents type shipment details into it; it clears the goods with HMRC.
The document a business actually holds is the customs declaration / entry — a human-readable copy (PDF or data export) produced from CDS. The real submission is structured electronic data (XML) sent software-to-HMRC.
A CDS import declaration is organised into 8 groups of data elements (the official name for fields); a full import declaration can need up to ~76–78 of them, depending on the declaration category (H1 is the standard type for a normal import into free circulation).
The content is standardised by HMRC (same fields), but the layout is not — every agent's software prints it differently and labels fields differently.
The fields the app needs, and where they live (always present on a standard import):
Commodity code — DE 6/14 (first 8 digits, mandatory)
Item price / value — DE 4/14
Invoice currency — DE 4/10
Exchange rate — DE 4/15 (conditional — only when the invoice is in foreign currency)
Country of (non-preferential) origin — DE 5/15
Net mass in kg — DE 6/1
Description of goods — DE 6/8
Importer identification / EORI — DE 3/16
Procedure code — DE 1/10 (e.g. 40 00 = release to free circulation)
Declaration type — DE 1/1 (IM = import)
Additional declaration type — DE 1/2 (e.g. Z = supplementary)
EORI = the importer's customs ID (starts "GB" + 12 digits).
"Present" does not mean "correct" — a mandatory field is there, but can still be wrong.

Links (official + learning):

CDS import declaration completion guide (Volume 3): https://www.gov.uk/government/publications/cds-uk-trade-tariff-volume-3-import-declaration-completion-guide — checked on: 2026-09-01
Alternate completion guide reference: https://www.gov.uk/government/publications/customs-declaration-completion-requirements-for-great-britain — checked on: 2026-09-01
Commodity code step-by-step (DE 6/14–6/17): https://www.gov.uk/hmrc-internal-manuals/customs-cds-volume-3-tariff-step-by-step-guide/cdssg08010 — checked on: 2026-09-01
HMRC CDS data descriptions (uktradeinfo): https://www.uktradeinfo.com/trade-data/request-customs-declaration-service-data-on-imports-and-exports/customs-declaration-service-data-import-and-export-descriptions/ — checked on: 2026-09-01
C4T "Ultimate Guide to CDS Data Elements" (PDF): https://4256821.fs1.hubspotusercontent-na1.net/hubfs/4256821/The%20C4T%20ultimate%20guide%20to%20the%20new%20CDS%20data%20elements%20.pdf — checked on: 2026-09-01
Multifreight CDS Trade Imports leaflet (PDF): https://multifreight.com/wp-content/uploads/2022/01/8266_CDS_Trade_Imports_Leaflet_v3_Accessible.pdf — checked on: 2026-09-01
"How to read a UK CDS customs entry" (easyclearance): https://easyclearance.pl/en/articles/cds-customs-declaration-jak-czytac-pola-uk.html — checked on: 2026-09-01
Worked CDS examples (customs-declarations.uk): https://www.customs-declarations.uk/category/customs-declarations-use-cases/cds-import-declarations/ — checked on: 2026-09-01
How we use it
The app can safely assume the core fields (code, value, currency, origin, weight, EORI, description, date) are always on a standard import declaration; it treats the exchange rate (4/15) as conditional.
The app must cope with different layouts across agents — the same fact appears in different places with different labels. Finding the fields in varied layouts is the real extraction work.
Sample documents we built for practice (see "Practice data") are modelled on the H1 standard type.
The commercial invoice (the other source document)
The source
The commercial invoice is the seller's bill. It is where value and currency originate (the seller sets them); the declaration then repeats them in official form.
Unlike the declaration, the invoice is not standardised — every supplier designs their own, so layouts vary wildly (different languages, formats, missing fields).
Fields an invoice usually carries: invoice number, invoice date, seller/exporter name + address, buyer/importer name + address, buyer EORI (sometimes), description of goods, commodity/HS code (often partial or absent), quantity, unit price, total value, currency, country of origin, net + gross weight, Incoterms (delivery terms, e.g. CIF), payment terms.
A single invoice can carry multiple goods-lines (steel + aluminium + packaging on one invoice).
The invoice and declaration are supposed to describe the same shipment but in real life often disagree (wrong code copied, value mismatch).
How we use it
The invoice is the app's source for the original price + currency; the declaration is the source for the official code, £ value and weight.
Cross-checking invoice against declaration and flagging disagreements is parked to October (decision 2026-09-01); v1 reads each uploaded document on its own. Catching mismatches remains part of the eventual job.
One row per goods-line (not per shipment), because scope is decided per goods-line.
Currency conversion
The source
The £50,000 threshold is measured in pounds. Foreign-currency invoices must be converted.
CDS converts foreign-currency values into GBP using HMRC's published monthly exchange rates — you must use the rate for the month of import, not today's rate, not the invoice's own rate.
HMRC updated the DE 4/15 exchange-rate instructions as recently as 22 January 2026.
HMRC publishes the monthly rates on the penultimate Thursday of each month; they apply to the following calendar month.

Links:

HMRC currency exchange monthly rates (view online, or CSV/XML): https://www.trade-tariff.service.gov.uk/exchange_rates/monthly — checked on: 2026-09-01
How we use it
The app stores a rate per month (not a single rate) and applies the correct month's rate to each foreign-currency goods-line before adding it to the running total.
Built in v1 (adopted 2026-09-01): a hand-kept data/exchange-rates.json — one rate per currency per month, copied from the link above, with the source link and a checked_on date inside the file. The intake step converts every non-£ line with its import month’s rate and stores the original value + currency, the £ value, and which month’s rate was used, so every converted number can show its working. Synthetic test data includes euro and dollar invoices; one hand-worked scenario in the test set covers conversion.
Getting the rate wrong quietly wrecks the whole total, so this is a dedicated, tested step.
The running total (the heart of the counter)
The source
A running total is a live sum that updates as each new in-scope shipment is added (like a shopping basket total).
For the UK it is a rolling total: only the last 12 months count, so as new shipments are added, ones older than 12 months drop off, and the window slides forward each month.
How we use it
The app is this running total — the live count nobody else is keeping.
It re-tests the rolling 12-month window as of the 1st of each month. (The 30-day forward check is October’s.)
It shows the bucket, the line, the fill rate, and the crossing date.
The dated monthly record (the "frozen" evidence)
The source
(Our design decision, grounded in the 2027/2028 gap.) A dated record of what the running total was, on what date, based on which documents, using which exchange rate, and which borderline calls were made.
How we use it
The app keeps each month's running total unchanged ("frozen"), so an answer given in June can still be shown in December.
This is the core evidence a business relies on during the 2027 liability-but-can't-register gap.
v1 decision (2026-09-01): parked to October to protect the 26 September deadline — v1 ships the live running total with receipts; the frozen monthly snapshot is first in line after v1 (the 2027-gap argument above is exactly why).
Tax calculation (what the counter does NOT do by default)
The source
Calculating the tax is a different, harder job than the counter. The counter answers "are you caught?" (value only); the calculator answers "how much do you owe?" (needs emissions data).
The formula: Tax = (weight of good × emission value) × carbon price − overseas carbon price already paid (Carbon Price Relief)
Emission value = how much CO₂ per tonne of product (a quantity, tonnes CO₂ per tonne of good). Depends on product + country of origin.
Carbon price = £ per tonne of CO₂ (a price). Set by HMRC per sector.
Weight comes from the customs declaration (kg, excluding packaging).
Overseas carbon already paid comes from the supplier, document by document — not a public table; for a worst-case estimate, set it to zero.
The tax is calculated from WEIGHT (tonnes), not value (pounds). Pounds decide whether you're caught; weight decides how much tax.
The two UK inputs needed here — UK default emission values and UK sector rates — are not published yet (see "Unpublished / pending items").
How we use it
The counter does not calculate final tax and never says "you are compliant."
v1 decision (2026-09-01): v1 shows no £ tax figure at all. It shows only the estimated CO₂ tonnes per goods-line and per month (weight × stand-in emission value), always badged ESTIMATE.
The £ skeleton (× carbon price − overseas carbon, worst-case with overseas = 0, labelled “for planning only”) is October’s; if built then, it uses the temporary stand-in values below until the UK numbers publish.
The app can hand off to a bigger tool / later module for real emissions work once a business is caught.
Emission values — UK not published, EU used as a temporary stand-in
The source
UK default emission values are not published yet (expected late 2026, ahead of the 1 Jan 2027 start).
Until they publish, we use the EU default emission values as a temporary stand-in, purely to test that the tax-estimate maths works. These are the "how much CO₂ per tonne" numbers (a quantity), organised by commodity code + country of origin. We already hold two copies of this data.
Critical read note: the official EU file uses commas as decimal points (European style) — 1,470 means 1.47 tonnes CO₂ per tonne, not one thousand four hundred. Misreading this is off by 1000×.
The per-country tabs give: code, description, direct emissions, indirect emissions (electricity), total emissions (direct + indirect, the number to use), and production route.
The values are "excl. mark-up" — a punishment mark-up is applied on top, not shown in the file.
The clean re-published version covers country-specific values but not the precursor values where country of production can't be identified — so it is convenient but not complete.

Links (stand-in source only):

Default values hub ("Default values definitive period (Excel format)"): https://taxation-customs.ec.europa.eu/carbon-border-adjustment-mechanism/cbam-legislation-and-guidance_en — checked on: 2026-09-01
Clean Excel version: https://carboneer.earth/en/2026/08/cbam-default-values-2026-excel/ — checked on: 2026-09-01

Files:

Official default values — one worksheet per country (121 countries) plus Overview, Version History, Annex IV.
Found at: the hub link above.
Filename: DV_correcting_act_final_update_06_08.xlsx
Repo folder: data/emission-values/
App reads: data/emission-defaults.json — one entry per covered commodity code (the total emissions value; worst-case route where several), built from this official file with the comma-decimal parsed correctly.
Clean flat version — one table, all countries stacked (22,180 rows, 572 codes, 121 countries).
Found at: the clean-Excel link above.
Filename: carboneer-20260731-cbam-default-values-reg-2026-1740.xlsx
Repo folder: data/emission-values/
App reads: nothing directly — this copy is for cross-checking the derived data/emission-defaults.json only.
How we use it
Used only as a temporary stand-in to test the tax-estimate maths while UK values are missing — the estimate is labelled "for planning only, using stand-in values."
Lookup key = commodity code + country of origin (both already captured per goods-line) → read the total emissions column.
The app must parse the comma-decimal correctly, and (if multiple production routes) either match the factory's route or take the worst-case (highest).
Swap-out plan: replace with the UK default values the moment HMRC publishes them; the stand-in exists only to build and test the pipeline.
Carbon price — UK not published, EU figure used as a temporary stand-in
The source
The UK sector rate (the carbon price) is not published yet (expected late 2026, close to each quarter).
Until it publishes, we use the EU certificate price as a temporary stand-in, purely to test the tax-estimate maths. It is published as a figure (not a downloadable file) and changes over time; an early-2026 figure was around 75 per tonne (ballpark).

Numbers we count with (stand-in only):

Stand-in carbon price: ~75 per tonne CO₂ (EU certificate price, early 2026, ballpark) — used only until the UK sector rate publishes.
https://taxation-customs.ec.europa.eu/carbon-border-adjustment-mechanism/cbam-communication-and-news_en — checked on: 2026-09-01
How we use it
Recorded only — not used by v1 (v1 shows no £ figure). When the £ skeleton is built (October), read the current figure from the source above (there is no static price file), and swap in the UK sector rate the moment it publishes.
Unpublished / pending items
The source
UK default emission values — not published as of mid-2026. Expected late 2026, ahead of 1 Jan 2027 (HMRC's wording is "ahead of 1 January 2027" — no exact date).
UK sector rates (the carbon price) — not published as of mid-2026. Expected late 2026, close to each quarter.
UK draft Emissions and Verification Regulations — still pending / being finalised as of mid-2026.
11 August 2026 consultation — proposed removing some of uktradeinfo's ready-made tables. Outcome not confirmed in our conversation. <TO CONFIRM> the outcome.
UK CBAM public register — does not exist yet; arrives with the scheme; whether outsiders can access it is <TO CONFIRM>.

Links to watch:

gov.uk CBAM collection (where UK defaults + rates will appear): https://www.gov.uk/government/collections/check-if-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam — checked on: 2026-09-01
How we use it (in the meantime)
Build the counter now using data that exists (scope list, thresholds, HMRC monthly exchange rates) — the counter needs none of the missing numbers.
Build the tax calculator as a skeleton using the stand-in emission values and carbon price (both above), clearly labelled; switch to real UK numbers the moment they publish.
Set gov.uk email alerts on the CBAM pages so we catch the numbers the day they drop.
Do not build anything long-lived on the specific uktradeinfo tables under consultation until the outcome is known.
Data sources for building and practice
The source
uktradeinfo — free UK national trade data by commodity code, Open Government Licence v3, no key/registration, returns up to 40,000 rows per pull, limited to about 60 requests per minute. It gives national aggregate data — not one company's own imports.
The business's own customs entries (held by the freight agent / in their own declarations) — the actual fuel for the counter. This is confidential and belongs to the business.
Bought trade-data vendors (Panjiva, ImportGenius, Datamyne) — real shipment records, but pre-cleaned, expensive, often missing £ invoice values, fragmented. Useful for finding prospects, not for building the counter.
Indian trade data (Zauba, Export Genius, Volza) — granular, sometimes previewable free; good for extraction practice on real-shaped data (especially given our India access), but it's the wrong country/border/threshold for the UK tool and is not a UK declaration.
HMRC publishes only aggregate national figures — never individual company records.

Links:

uktradeinfo: https://www.uktradeinfo.com — checked on: 2026-09-01
Directory of small customs agents (GoodFirms): https://www.goodfirms.co — checked on: 2026-09-01
Directory "customs clearance agents UK for small importers" (europe.express): https://europe.express — checked on: 2026-09-01
BIFA member directory (freight association): https://www.bifa.org — checked on: 2026-09-01
How we use it
uktradeinfo → build and sanity-check our scope list, benchmark, understand the landscape — not as a business's own shipments.
The business's own customs data (via the agent) → the real input for the counter.
Indian data → realistic extraction practice only; kept in its lane.
Bought vendors → parked for now (too expensive; skips the reading skill); possibly a prospect-finding tool later.
Practice data (fake first, real later)
The source
(Our decisions.) The plan: fake data first → build the product on it → iterate with real data later.
Fake data proves the machine works (counting, currency conversion, rolling window, scope check). It does not teach the real-world mess you haven't imagined — that only comes from real documents.
Four data sets in the project: importer record, shipments (the heart, one row per goods-line), scope list (real, copied from Annex B), rules/rates (thresholds real; carbon price + emission values via stand-ins until UK publishes).
The transform step (messy input → clean rows) is the hard, valuable core: Extract → Transform → Load ("ETL").
Traps to plant deliberately in fake shipments: mixed currencies, missing/partial codes, wrong/borderline codes, different date formats, duplicates, out-of-scope goods mixed in, multi-goods lines, odd/missing weights, inconsistent value formatting.
Sample source documents already built for practice: a full H1 declaration and a matching commercial invoice (fictional "Meridian Fixings Ltd" importing steel brackets — illustrative data).
How we use it
Write the answer key first — for every fake row, record the correct scope decision and the correct running total before building the tool, so we can tell if the output is right. Skipping this is the #1 trap.
First batch: ~20–30 goods-lines for one importer over 12 months, sized to cross £50,000 so the warning fires. Bigger batches only after the logic works on the small set.
Build the first batch by hand; use a generator (e.g. Faker library, or Mockaroo) or AI only later to scale.
Keep the real-sample hunt running in parallel — the fake set is a rehearsal, never a substitute for one real document.
Getting real documents (routes and decisions)
The source
Real, un-redacted import documents are confidential and legally belong to the importer — so almost nobody can "give" them to us.
An importer (their own documents) — can legally share; the only route to a complete real set. We currently have no network importer.
A freight agent / broker — can share redacted documents only (content belongs to their clients); a professional won't hand over raw client data.
A paid broker hour — the most reliable route: pay a broker to show/walk through redacted real entries and explain the format. A transaction, not a favour.
HMRC — cannot share individual records; only aggregates.
Customs training course/module — realistic but clean, taught examples (a cheap intro CDS module, not the expensive agent qualification).
Public samples/templates — real format, not real mess (C4T, Multifreight).
How we use it (decisions)
Fake data first → build → iterate with real data later. (Locked-in plan.)
Ask agents/brokers only for redacted samples; never push anyone to share a client's confidential data (a red flag ethically and legally for us).
Run two threads in parallel while building: the paid broker hour (reliable redacted samples) and cold outreach (to agents for the channel; possibly to small importers directly for a complete set).
The framing to a broker is "show me what a real declaration/invoice looks like — redacted is fine — and walk me through the format," not "give me your client data."
Go-to-market and outreach (decisions)
The source
The strongest channel is the freight agent: they see every import, have many small-importer clients, and one relationship reaches ~50 businesses. They'd sell a running total, not advice.
The value-first hook for agents: their clients will wrongly assume "my agent handles CBAM," but liability is the importer's (Finance Act 2026, s.146) — agents need this straight, and the 2027/2028 gap is a real trap most don't know about.
Outreach is a numbers game — most ignore cold contact; a few reply; one or two engage. Message 15–20 to get 2–3 conversations. The first message's only job is a reply, not data or a sale.
We are not targeting by industry — the counter works the same across all CBAM goods; the target is any agent with small-importer clients.
We do not claim to be from a company; honest "recent graduate exploring/building something" framing. Don't claim conversations we haven't had.

Firms shortlisted (public contacts, verify on their own sites):

Dover Transit — info@dovertransit.co.uk — https://dovertransit.co.uk — checked on: 2026-09-01 (email came via a directory; verify)
UK Import Services — enquiries@ukimportservices.com — https://ukimportservices.com — checked on: 2026-09-01
FF Customs & Logistics — office@ffcl.co.uk / sales@ffcl.co.uk — https://ffcl.co.uk — checked on: 2026-09-01
Brunel Shipping — info@brunelshipping.co.uk — https://brunelshipping.co.uk — checked on: 2026-09-01
Customs Clearance UK (Eddie Maybank) — contact form/phone — https://customsclearance.uk.com — checked on: 2026-09-01
Simply Customs, Smart Customs UK (https://smartcustoms.uk), Grange Shipping (https://grangeshipping.co.uk), Octain Logistics — via their sites — checked on: 2026-09-01
How we use it
Emails sent to the four public-email firms; LinkedIn connection requests + follow-ups queued (two-step: short note, then fuller message once accepted).
Track everything in a sheet: Firm · Email · LinkedIn sent · Accepted? · Replied? · Next step.
Recorded as parked / in progress: reply-handling playbook (what to say when someone responds, and how to steer toward a redacted sample) — not yet written.
Competitor landscape
The source
Two camps:
CBAM-only specialists (whole product is CBAM): CBAMBOO, Cbamboo, Kolum, Dubrink.
Broad platforms (CBAM is one feature): Sphera, Normative, CarbonChain, Sinai, Assent, Watershed, Persefoni, Greenly, Plan A, IBM Envizi, Breathe ESG.
How the notable ones get supplier emissions data:
CarbonChain — built a library of asset-level emission-factor estimates (metals/energy) first (the moat), then added a Supplier Catalogue for real verified data; founded 2019, ex-Rio Tinto/BCG/Amazon, Y Combinator seed + InnovateUK grant. Doc-reading tech turns shipping documents into the lookup key (what/quantity/origin), not emissions.
CBAMBOO — no big database; a shared workspace where the supplier self-calculates using the official method. Tiny (~6 people, ~£1.12m). Pricing reportedly from ~€9,000/year; explicitly points small importers elsewhere.
Sphera — enterprise software plus consultants; grew supplier-data ability by acquisition.
Normative, Sinai, Assent — broad carbon platforms; general supplier data collection with CBAM as one output.
The three ways anyone gets a factory's number: ask the factory (verified), estimate from a database (emission factors), or use the regulator's default. No paid tool sells "just use the default."
The gap we target — a cheap counter for small importers who don't know if they're caught — is underserved by both camps, but it's a feature-shaped gap, easy for an incumbent to add. Defence = small-importer focus + freight-agent channel.
How we use it
Confirms our positioning: counter, not calculator; small importers, not enterprise; channel as the moat.
Note (to re-verify, not assume): an earlier claim that Coolset "moved on" was contradicted by later signs it was still publishing CBAM material in 2026. <TO CONFIRM> Coolset's current status.
Legal / evidence lines the app must hold
The source
(Our decisions, grounded in the rules above.)
How we use it
On screen, always: we count what the paperwork says and nothing more; deciding a commodity code is a customs judgement, not ours; we are not customs agents or tax advisers and not authorised to act for anyone; the scheme is new and rules still move; every answer carries the date it was worked out; any tax figure is a stand-in-based estimate for planning only.
Never mark a shipment as settled without either evidence or an explicit, named, dated human statement.
Never file anything on anyone's behalf.
Business import records are commercially sensitive even though there's little personal data — access must be limited and secured.
Lean towards warning early and saying plainly when unsure (a false "you're safe" is far worse than a false "you're over").
Parked items (recorded, not in v1)
The source & decision
Tax calculator — parked as a skeleton, running on stand-in values, until UK rates + defaults publish; only ever a "for planning only" estimate even then.
Supplier-emissions / "follow suppliers" feature — parked as a separate, harder module for bigger clients later, not part of the core counter (nobody can measure factory pollution from outside; leverage is the problem; small importers have almost none).
Bought trade-data vendors — parked (too costly; skips the reading skill); possible prospect-finding tool later.
Reply-handling playbook for outreach — parked; not yet written.
30-day forward test — parked to October (needs an expected-imports input; decision 2026-09-01).
Frozen monthly record — parked to October (decision 2026-09-01) despite the build-early argument in its section; first in line after v1.
Invoice↔declaration cross-check — parked to October (decision 2026-09-01).
£ tax estimate (skeleton) — parked to October (decision 2026-09-01); v1 shows CO₂ tonnes only.
Creative supplier-data ideas (buyers' club, shared verified-factory directory, group verification, piggyback existing factory reports, defaults-only forecast, satellite datasets, factory-publishes-its-own-number) — parked as strategy only; each needs a legal check on the specific mechanic (especially reusing one importer's verified number for another) before building.
Monthly check

Run this on the 1st of each month. Open every link below, confirm nothing has changed (rules, thresholds, dates, files), and refresh the checked on: date wherever the content still holds. Where something has changed, update the relevant section and note what changed.

 UK register-date guidance (thresholds, two tests, 2027/2028 gap): https://www.gov.uk/guidance/work-out-the-date-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam
 UK CBAM collection (watch for UK default values and sector rates publishing — the two stand-ins to replace): https://www.gov.uk/government/collections/check-if-youll-need-to-register-for-carbon-border-adjustment-mechanism-cbam
 UK "check which goods are in scope" + Annex B codes (re-check before any real client work — it changes): https://www.gov.uk/government/publications/check-which-goods-are-in-scope-of-carbon-border-adjustment-mechanism-cbam
 Commodity-code lookup tool: https://www.gov.uk/trade-tariff
 CDS import declaration completion guide (field numbers/mandatory set): https://www.gov.uk/government/publications/cds-uk-trade-tariff-volume-3-import-declaration-completion-guide
 HMRC monthly exchange rates — copy the new month’s rates into data/exchange-rates.json: https://www.trade-tariff.service.gov.uk/exchange_rates/monthly
 uktradeinfo (confirm access + the 11 Aug 2026 consultation outcome on ready-made tables): https://www.uktradeinfo.com
 Stand-in emission values — check whether the UK values have published yet (if so, swap out the stand-in); otherwise confirm the stand-in file is still current: https://taxation-customs.ec.europa.eu/carbon-border-adjustment-mechanism/cbam-legislation-and-guidance_en
 Stand-in clean Excel (re-download if the underlying file was corrected): https://carboneer.earth/en/2026/08/cbam-default-values-2026-excel/
 Stand-in carbon price — check whether the UK sector rate has published yet (if so, swap out the stand-in); otherwise note the current figure: https://taxation-customs.ec.europa.eu/carbon-border-adjustment-mechanism/cbam-communication-and-news_en
 Resolve any remaining <TO CONFIRM> items in this file.

Standing reminders:

The UK default values and UK sector rates are the two numbers still missing — the tax estimate stays "for planning only, using stand-in values" until both are live, then swap the stand-ins out.
Re-download the stand-in emission-value Excel if a correction is issued (last correction referenced: 2026-07-31).
Re-check the Annex B scope list before any real client work — it changes.

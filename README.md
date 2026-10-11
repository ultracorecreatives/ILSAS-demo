# ILSAS Prototype: Review Guide

**ILSAS** (Interconnected Land Services Audit System / আন্তঃসংযুক্ত ভূমি সেবা নিরীক্ষা ব্যবস্থা) is a clickable **demo** of a government audit portal. It shows how an auditor would:

1. compare land records across systems (e-Mutation, LD Tax, LARMS, Lease, Land Data Bank),
2. raise an audit objection (আপত্তি), and
3. follow that objection until it is settled: office reply → DAC meeting → PAC.

It is a prototype for showing to stakeholders and collecting feedback. **Nothing is saved, nothing is sent and all data is made up.** Reloading the page resets everything.

---

## 1. What is in this folder

| File / folder | What it is | Do you need to open it? |
|---|---|---|
| **`ILSAS Bangla Portal.dc.html`** | **The prototype itself.** | **Yes. This is the file to open.** |
| `index.html` | Start page for web hosting (GitHub Pages). It opens the prototype automatically | No |
| `README.md` | This guide | You are reading it |
| **`manual/ILSAS ব্যবহার নির্দেশিকা.pdf`** | Bangla user manual with 17 screenshots, for end users | Yes, share this with users |
| `manual/ILSAS ব্যবহার নির্দেশিকা.md`, `manual/screenshots/` | Editable source of the manual and its images | Only if the manual needs changes |
| `support.js` | Engine that makes the page work | No, but it must stay in the same folder |
| `_ds/` | Colours and styles | No, but it must stay in the same folder |
| `uploads/Workflow v1.0.docx` | The workflow specification the prototype was built from | Optional reference |
| `ILSAS Bangla Portal.zip` | Everything above in one file, for sending to others | Only for sharing |
| `.thumbnail`, `.DS_Store` | System files | No, ignore them |

> ⚠️ Keep the files together. If you move only the `.html` file to another place, the page will not work.

---

## 2. How to open it

**Option A: double-click (try this first)**
1. Double-click `ILSAS Bangla Portal.dc.html`.
2. It opens in your web browser. Google Chrome works best.
3. You need an internet connection, because the Bangla fonts load from Google.

**Option B: if the page is blank or looks broken**
1. Open the **Terminal** app on a Mac.
2. Type `cd ` (with a space after it), drag this folder into the Terminal window, then press **Enter**.
3. Paste this and press **Enter**: `python3 -m http.server 8000`
4. In Chrome, go to: `http://localhost:8000/ILSAS%20Bangla%20Portal.dc.html`
5. When you are finished, close the Terminal window.

If neither option works, ask the development team for help.

**If you received the zip:** unzip it first, then follow the steps above.

---

## 3. Demo login

The login details are already filled in. You only need to click.

| Field | Value |
|---|---|
| User ID | Filled in automatically when you choose a role |
| Password | already filled |
| OTP code | Any code works. You can also leave it empty and click **যাচাই ও প্রবেশ** |
| Role (পদবি / স্তর) | **Choose one.** Each role opens a different starting page (see below) |

| Role you choose | Demo user (name · ID) | Page you land on |
|---|---|---|
| কেন্দ্রীয় নিরীক্ষা কর্মকর্তা (Central Audit Officer) | সাইফুল আলম · ADT-0142 | Dashboard, all districts |
| জেলা নিরীক্ষা কর্মকর্তা (District Audit Officer) | নাসরিন সুলতানা · ADT-0217 | Dashboard titled for Gazipur district |
| উপজেলা নিরীক্ষা পরিদর্শক (Upazila Audit Inspector) | মোঃ রাকিবুল হাসান · ADT-0385 | Dashboard titled for Kaliakair upazila |
| দপ্তর প্রতিনিধি (জবাবদাতা) (Office Representative) | ফারহানা ইয়াসমিন · OFC-1103 | Objection Settlement page |
| DAC কমিটি সদস্য (DAC Committee Member) | মোঃ জাহিদ হোসেন · DAC-0021 | Objection Settlement page |
| মন্ত্রণালয় প্রতিনিধি (Ministry Representative) | শাহনাজ পারভীন · MIN-0056 | Objection Settlement page |
| কারিগরি প্রশাসক (Technical Admin) | তানভীর আহমেদ · SYS-0003 | Reports & Audit Log page |

### Who can see and do what

Each role sees only its own menu pages, only its own jurisdiction's objections, and only the buttons for its own step.

| Role | Pages in the menu | Objections it can see | What it can do |
|---|---|---|---|
| Central Audit Officer | Dashboard, Cross-verification, LARMS, Settlement, Reports | All | Raise objections, attach evidence, schedule inspections, flag claimants, **send unsettled objections to PAC** |
| District Audit Officer | Dashboard, Cross-verification, LARMS, Settlement, Reports | Gazipur district only | Raise objections, attach evidence, schedule inspections, flag claimants |
| Upazila Audit Inspector | Dashboard, Cross-verification, Settlement, Reports (**no LARMS**) | Kaliakair upazila only | Raise objections, attach evidence, schedule inspections |
| Office Representative | Settlement only | Objections sent to AC (Land), Kaliakair only | **Reply** (draft / final) with attachments |
| DAC Committee Member | Settlement, Reports | All | Schedule DAC meeting, **DAC decision**, generate minutes |
| Ministry Representative | Settlement, Reports | All | Upload ministry explanation, **record PAC decision** |
| Technical Admin | Reports only | All | View reports and audit trail |

- When a step belongs to another role, its buttons are hidden and a grey note says who acts there (e.g. "এই ধাপের কাজ করবেন: দপ্তর প্রতিনিধি").
- Opening a page that isn't allowed (e.g. clicking the LARMS card as Upazila Inspector) shows **প্রবেশাধিকার নেই** with a button back to the role's start page.
- The Settlement and Reports pages show **"আপনার অধিক্ষেত্র: …"** so you know which data you are looking at.

---

## 4. Review checklist

Work through each section. Tick ☐ → ☑ when the result matches. If it does not, note it (see section 7).

### A. Public home page (হোম)
- ☐ The header shows the Government of Bangladesh / Ministry of Land branding.
- ☐ There are **9 service cards**: e-Mutation, LD Tax, Land Record, LARMS, Lease, Land Administration, Revenue Case, Land Data Bank and Grievance.
- ☐ Clicking a service card or the search box asks you to **log in first**.
- ☐ Clicking **English** (top right) shows a message that English is not in this demo.

### B. Login (নিরীক্ষক লগইন)
- ☐ Click **নিরীক্ষক লগইন** → you see User ID, Password and Role, plus **Forgot password** and **Technical support** links.
- ☐ Click **ওটিপি যাচাইয়ে যান** → an OTP box appears.
- ☐ Click **যাচাই ও প্রবেশ** → you are logged in and a green message appears in the bottom-right corner.
- ☐ Log out (**প্রস্থান**, top right) and log in again with a different role. The starting page changes as shown in the table in section 3.

### C. Dashboard (ড্যাশবোর্ড)
- ☐ **5 number boxes** at the top: total audited, flagged discrepancies, revenue shortfall, settled objections, pending field inspections.
- ☐ 9 service cards, each showing how many problems were flagged.
- ☐ **Cross-verification rules** table: clicking a row opens the comparison screen.
- ☐ **Awaiting settlement** table (উচ্চতর নিষ্পত্তির অপেক্ষায়): clicking a row opens that objection on the Settlement page.
- ☐ **Bell icon** (top right, with a red number) → opens a list of reminders: overdue replies, deadlines coming up, replies received and the next DAC meeting. Clicking a reminder opens that objection.

### D. Cross-verification & raising an objection (ক্রস-ভেরিফিকেশন)
- ☐ The screen is split: the source record is on the left and the matched record from the other system is on the right. Mismatched values are shown in **red**.
- ☐ The **discrepancy table** below lists each mismatch with a severity (অতি গুরুতর / গুরুতর / মাঝারি / সামান্য).
- ☐ **প্রমাণক সংযুক্ত করুন** (attach evidence) → the evidence count goes up.
- ☐ **সরেজমিন তদন্তের সময়সূচি** (schedule field inspection) → a confirmation message appears.
- ☐ **আপত্তি উত্থাপন** (raise objection) → a form opens with description, **objection type** (financial / administrative / procedural), severity, recipient office and deadline.
- ☐ Submit it → a message shows a new reference number, e.g. `AO/GAZ/2026/0413`.
- ☐ Tip: type `604` in the top search box and press Enter to see the **Lease vs Land Data Bank** comparison instead.

### E. LARMS audit (LARMS নিরীক্ষা)
- ☐ A progress bar shows the acquisition stages, from proposal to compensation.
- ☐ There are **5 tabs**: Proposal, Cha-Form & schedule, Joint survey, Notices 4(1)/7(1), Compensation tracker.
- ☐ The Compensation tab lists claimants and shows who is paid, partly paid or unpaid.
- ☐ Click **চিহ্নিত করুন** (flag) on an unpaid claimant → confirm → that row changes to "flagged".

### F. Objection settlement (আপত্তি নিষ্পত্তি). **New in this update**
This page follows each objection through the official process from the proposal document.

```
Objection raised → Office replies → DAC reviews → DAC decides ─┬─ Settled (done)
   (Audit team)     (Office rep)    (DAC committee)            ├─ Re-examine (office replies again)
                                                                └─ Unsettled → PAC → Settled / Disciplinary action
```

- ☐ The top boxes show Total, Replied, Settled, Unsettled/PAC and **Overdue**.
- ☐ The **Objection register** on the left lists every objection with its deadline ("X days left" or "X days overdue", in red) and its current stage.
- ☐ Clicking a row shows its details on the right: a 5-step progress strip, **"এখন কী করতে হবে" (what happens next)** and its history.
- ☐ The objection you raised in step D appears at the top of the register.

**Walk one objection through the whole process** using `AO/GAZ/2026/0412`. Log out (**প্রস্থান**) and log in as the role named in each step. Your work carries over between roles.
1. ☐ **Office reply** (log in as **দপ্তর প্রতিনিধি**): type an explanation, click **প্রমাণপত্র সংযুক্ত** (attach), then **চূড়ান্ত জবাব দাখিল** (submit final reply). You can also click **খসড়া সংরক্ষণ** (save draft) to keep it without submitting.
2. ☐ **DAC decision** (log in as **DAC কমিটি সদস্য**): three buttons appear: **নিষ্পত্তি** (Settled), **পুনঃনিরীক্ষণ** (Re-examine) and **অনিষ্পন্ন** (Unsettled).
   - Settled → the objection is closed.
   - Re-examine → it goes back to the office for more proof.
   - Unsettled → continue to step 3.
3. ☐ **Send to PAC** (log in as **কেন্দ্রীয় নিরীক্ষা কর্মকর্তা**): click **CAG-এর মাধ্যমে PAC-এ প্রেরণ**.
4. ☐ **PAC decision** (log in as **মন্ত্রণালয় প্রতিনিধি**): click **PAC: নিষ্পত্তি** (settled) or **PAC: শৃঙ্খলামূলক ব্যবস্থার নির্দেশ** (disciplinary action).
5. ☐ Each step adds a line to the objection's **history**.
- ☐ Choose a **DAC meeting date** → click **সভা নির্ধারণ ও নোটিশ** (DAC member) → a confirmation message appears.
- ☐ Click **কার্যবিবরণী (MoM) তৈরি** (DAC member) → draft meeting minutes appear, listing the DAC decisions you made.

### G. Reports & audit log (প্রতিবেদন ও লগ)
- ☐ Filters: date range, district, service, severity and **objection type**. The table updates when you change a filter.
- ☐ The status column matches each objection's stage on the Settlement page.
- ☐ **পিডিএফ প্রতিবেদন তৈরি** → a summary box shows the number of findings and the **total money involved**. The total matches the sum of the amounts in the table.
- ☐ CSV export and Print Certificate buttons show a confirmation message.
- ☐ **Audit trail** (অপরিবর্তনীয় অডিট ট্রেইল) at the bottom: everything you did in this session is listed with a time.

---

## 5. How the prototype matches the two source documents

**Source 1:** *Workflow v1.0 — ILSAS UI/UX & Workflow Specification* (English)
**Source 2:** *অডিট আপত্তি দাখিল ও নিষ্পত্তি প্রক্রিয়ার ডিজিটাল রূপান্তর প্রস্তাবনা* (Bangla proposal, Ultracore)

✅ = shown in prototype  ⚠️ = partly shown  ❌ = not in prototype (planned for the real system)

| Requirement | Source | In prototype |
|---|---|---|
| Login with role selection + OTP | 1 · Screen 1 | ✅ |
| Forgot password / helpdesk links | 1 · Screen 1 | ⚠️ Links are shown but do nothing |
| Bangla / English toggle | 1 · Screen 1 | ⚠️ Bangla only. The English link shows a notice |
| Role-based access (pages, data, actions) | 1 · §1.3, 2 · §4.2.1 | ✅ Pages, jurisdiction and buttons are restricted per role. Jurisdictions are fixed for the demo |
| All 7 user types (auditors, office rep, DAC, ministry, admin) | 1 · §1.3, 2 · §4.2.1 | ✅ Selectable at login |
| Single Sign-On (SSO) | 2 · §4.2.1 | ❌ |
| Dashboard KPIs, 9 service cards, global search | 1 · Screen 2 | ✅ |
| Notifications bell | 1 · Screen 2, 2 · §4.2.7 | ✅ |
| Settings page | 1 · Screen 2 | ❌ |
| Split-screen cross-verification + discrepancy matrix | 1 · Screen 3 | ✅ (2 sample cases: e-Mutation↔LD Tax, Lease↔Land Data Bank) |
| Raise objection with evidence, severity, deadline, recipient | 1 · Screen 3, 2 · §4.2.2 | ✅ |
| Objection type (financial / administrative / procedural) | 2 · §4.2.2 | ✅ |
| Automatic reference number | 2 · §4.2.2 | ✅ |
| Real file upload (PDF / Excel / image) | 2 · §4.2.2–4.2.3 | ⚠️ The button only increases a counter |
| LARMS 5 tabs + lifecycle bar + compensation tracker | 1 · Screen 4 | ✅ |
| Office reply form, draft / final, "Reply Submitted" | 2 · §4.2.3 | ✅ |
| DAC meeting: schedule, 3 decisions, minutes (MoM) | 2 · §1.4.2, §4.2.4 | ✅ (MoM shown on screen. PDF export not real) |
| PAC forwarding, ministry document, PAC decision | 2 · §1.4.3, §4.2.5 | ✅ |
| Raised / Responded / Settled / Unsettled counts | 2 · §4.2.6 | ✅ As number boxes (not graphs) |
| Overdue list + deadline reminders | 2 · §3.1.7, §4.2.6–4.2.7 | ✅ |
| Real email / SMS sending | 2 · §4.2.7 | ❌ Shown as messages only |
| Report filters, PDF / CSV / certificate export | 1 · Screen 5, 2 · §4.2.6 | ⚠️ Filters work. Exports only show a message |
| Monthly / yearly summary reports | 2 · §4.2.6 | ❌ |
| Audit trail log | 1 · Screen 5 | ✅ |
| Archive search by year / office / type | 2 · §4.2.8 | ⚠️ Filters by date, district, service, type and severity. No multi-year archive |
| "Similar objections" analysis report | 2 · §4.2.8 | ❌ |
| Biometric login | 1 · Step 1 | ❌ Mentioned in text only |

Items marked ❌ or ⚠️ are expected in a prototype. Confirm with the team whether any of them must be shown **before** the stakeholder demo.

---

## 6. Things that are not real (please don't report these as bugs)

- All names, NID numbers, case numbers and amounts are **made up**.
- "Today" inside the demo is fixed at **20 September 2026**, so that deadlines and "days overdue" always look the same.
- Nothing is saved. **Reloading the page resets everything.**
- No emails, SMS or files are really sent, uploaded or downloaded.
- Each role has one fixed demo user and jurisdiction (district = Gazipur, upazila/office = Kaliakair). District and upazila dashboard figures are scaled down from the national figures for the demo.
- The work you do is kept when you log out and log in as another role, so you can pass one objection from role to role. Reloading the page resets it.
- Links in the footer and the top bar (National Portal, Citizen Charter and so on) do nothing.

---

## 7. How to give feedback

For each problem or suggestion, write down:

```
Page:        (e.g. আপত্তি নিষ্পত্তি)
What I did:  (e.g. clicked "অনিষ্পন্ন" on AO/GAZ/2026/0389)
What I expected:
What happened:
Screenshot:  (optional but helpful)
```

---

## 8. Change log

**12 Oct 2026 (update 4)**: Added a red "ডেমো প্রোটোটাইপ — এটি প্রকৃত সরকারি সাইট নয়" banner on every page, a do-not-index tag, and `index.html` for GitHub Pages hosting.

**12 Oct 2026 (update 3)**: Each role now has its own demo user (name, initials, ID), and the audit trail shows who did each action. Fixes: going to the portal home no longer looks logged out; records outside a user's jurisdiction are blocked; dashboard figures are scaled to the district or upazila; cards and rules the role can't open are dimmed and marked "প্রবেশাধিকার নেই"; search and the bell are hidden for roles that can't use them; logged-out visitors see national figures. Manual: added a demo users table and removed the help/feedback section.

**12 Oct 2026 (update 2)**: **Role-based access.** Each role now sees only its own pages, its own jurisdiction's objections and its own step's buttons. Other pages show a "no access" message. Bangla text corrected (spelling, hyphenated suffixes, terms: পুনঃনিরীক্ষণ (from the Bangla proposal) and অনিষ্পন্ন for Unsettled (the usual term in government audit documents; the proposal says অবশিষ্ট), official law names). Bangla user manual with screenshots added in `manual/`.

**12 Oct 2026**: Checked the prototype against both source documents and added what was missing:
- **New page: আপত্তি নিষ্পত্তি (Objection Settlement).** Covers office reply (draft / final), DAC decision (Settled / Re-examine / Unsettled), meeting scheduling, auto minutes (MoM), PAC forwarding and PAC decision, with a history for each objection.
- **Notifications bell** with overdue and deadline reminders.
- **Three new login roles:** Office Representative, DAC Committee Member, Ministry Representative. Each role now opens its own starting page.
- **Objection type** added to the objection form and as a filter in Reports.
- Reports: the **date filter now works**. The **money total is now the real sum** (before, it was a made-up figure). The status column now follows the settlement stage.
- Dashboard: rows in "Awaiting settlement" now open that objection.
- The English link now explains that English is not in this demo (before, it did nothing).
- The audit trail now starts at login, and its times match the dashboard's "last updated" time.
- The zip file was rebuilt to include these changes.

# Intent: the Accountable MVP for a motorcycle dealership

## Problem

A small independent motorcycle dealership gets buyer enquiries from many places at once: AutoTrader, MotoMedia, WhatsApp, Instagram, Facebook, the phone and people walking in. Each one lands in a different inbox or on a different phone. Nobody can see at a glance which enquiries haven't had a reply yet, who promised to call whom back, or which buyers were interested in a bike that has just sold. Enquiries slip through. A buyer who hears nothing walks away, the bike sells to someone else, and the dealership earns a public one-star review for not calling back. Each lost buyer is a lost sale worth R40,000 to R320,000.

The workshop has the same gap. Service bookings sit in a diary or someone's head, and the shop can't easily see what's due in today, what's waiting on parts, or which customers need a call to say their bike is ready.

## Proposed outcome

Accountable is a business management system: a sales CRM that will grow into a full Business OS, including ERP. This first version, the MVP, is a sales and workshop CRM for a motorcycle dealership. It runs on one shared computer at the sales desk. Its single job is that **no enquiry goes unanswered and no promised callback is forgotten**. It should feel sharp, modern and professional, and be a pleasure to use on a busy shop floor.

### Six sections

- **Dashboard**, the landing page: how the shop is doing at a glance, with response speed first. It shows:
  - enquiries still waiting for a first reply, oldest first, with how long each has waited;
  - the share of enquiries answered within the response target, this week and month by month;
  - callbacks due today and overdue;
  - enquiries by source (which portals and channels bring buyers);
  - bikes sold and sales revenue month by month;
  - the open enquiry pipeline and its expected revenue (each enquiry's bike price times its probability of sale), with a funnel showing how many enquiries reach each stage;
  - today's workshop bookings;
  - recent activity.

  It should be visually stunning, with at least a line chart, a bar chart and a visual of the pipeline. Which figures each chart shows, and how, is the designer's call.
- **Enquiries**: every buyer enquiry, whatever channel it came in on. Each one shows the customer, the bike they asked about, the source, the stage, who it's assigned to, and when it was received. An enquiry that has had no first reply within the response target stands out, in the table and on its board card, and shows how long it has waited. Open an enquiry to see its details, its bike and its timeline. Adding an enquiry is quick enough for a busy Saturday: typing a name or mobile number in the form shows matching customers to pick, or a new customer is created from the same form, and a mobile number that's already on file is flagged so the same buyer isn't added twice. An enquiry moved to Lost needs a reason (bought elsewhere, price, finance declined, trade-in value, went quiet, bike sold to someone else, or other), and the reason shows on the enquiry.
- **Board**: the enquiries as cards, one column per stage. It shows every open enquiry, but the Sold and Lost columns show only enquiries closed in the last 30 days, so the board stays short; older ones are in the Enquiries table. Drag a card to another column to change the enquiry's stage, or within a column to change its place. A card can be dropped anywhere in a column, and it stays where it was dropped. A new enquiry can be added straight into a column, at that stage. The board shows the total value and expected revenue of the open enquiries, each column shows its own, and the figures change as soon as a card moves.
- **Stock**: the bikes for sale. Each bike has its stock number, make, model, year, mileage, price, status (available, reserved or sold) and which portals it is listed on. Filter by status, and by "not listed on" a portal, so a bike missing from AutoTrader or MotoMedia is easy to spot. Open a bike to see every enquiry about it.
- **Customers**: the people we deal with, buyers and workshop customers alike, with a filter by status (lead, customer). Open one to see their enquiries, their workshop bookings, the bikes they own and a timeline of everything that has happened with them. The bikes they own come from their history: the stock bikes they bought here and the bikes on their workshop bookings, each listed once, matched by registration.
- **Workshop**: service and repair bookings. Each booking has the customer, their bike (make, model and registration), the job, the booked-in date and a status (booked, in the workshop, waiting for parts, ready for collection or collected). By default it shows today's and this week's bookings, and it can show any day. When a booking is marked ready for collection, a "call to collect" callback is created by itself.

Every table has a search box, columns you can sort by clicking their headings, a way to add a new record, and edit and delete on each row. Deleting asks first, and says what will happen to the records linked to the one being deleted, with how many there are:

- deleting a customer also deletes their enquiries, workshop bookings and activities;
- deleting an enquiry or a workshop booking also deletes its activities;
- deleting a bike keeps its enquiries, with the bike kept on each one as a text description.

From any enquiry, customer or workshop booking you can log an activity (a note, call, WhatsApp, email or visit) and give it a callback date and the person it's assigned to. A callback shows on the dashboard as a task until it's marked done. Activities can be edited and deleted too.

Some things happen by themselves, so nothing relies on someone remembering:

- Logging the first call, WhatsApp, email or visit on a New enquiry records its first-response time and moves it to Contacted, and the enquiry stops standing out. Only a logged contact counts as the first reply: dragging a New enquiry to Contacted opens the form to log one, and the card stays in New if nothing is logged.
- When an enquiry moves to another stage, including Sold or Lost, an entry such as "Moved from Viewing booked to Test ride" appears in its timeline and in the dashboard's recent activity.
- An enquiry and its bike stay in step. Moving an enquiry to Sold marks its stock bike sold. Marking a bike sold on the Stock page asks which of its open enquiries won and moves that one to Sold, or records that the bike sold without one.
- When a bike is sold, either way, every other open enquiry about that bike gets a callback due today, "Bike sold: call back and offer alternatives", assigned to the enquiry's salesperson, and a note in its timeline. Nobody who asked about a bike finds out it sold by hearing nothing.
- A lead becomes a customer when one of their enquiries is marked Sold or they get a workshop booking. Staff can still change the status by hand.

### Six kinds of record

- **Customer**: a person we deal with. Name, mobile number, email, preferred contact channel (call, WhatsApp or email), and a status (lead or customer). A lead is a customer with the lead status, so there's no separate list of leads.
- **Bike**: a bike in stock. Stock number, make, model, year, mileage, registration (optional, so a bike sold here can be matched to the same bike in the workshop), price in rand, status (available, reserved or sold), the portals it's listed on (AutoTrader, MotoMedia) and notes.
- **Enquiry**: a buyer's interest in a bike. The customer, the bike (or a free-text description when it isn't a stock bike), the source (AutoTrader, MotoMedia, WhatsApp, Instagram, Facebook, phone, walk-in or referral), when it was received, when it was first answered, who it's assigned to, whether a trade-in or finance is involved, its stage (New, Contacted, Viewing booked, Test ride, Offer and finance, Sold or Lost), the reason it was lost (when it was), its value in rand (the bike's price unless set by hand), its probability of sale and its expected or actual sale date. Each stage has a usual probability of sale, fixed in the MVP: New 10%, Contacted 20%, Viewing booked 40%, Test ride 60%, Offer and finance 80%, Sold 100% and Lost 0%. An enquiry takes its new stage's probability when it moves. A probability set by hand is kept until the stage changes.
- **Workshop booking**: a service or repair. The customer, the bike (make, model, registration), the job description, the booked-in date, the status, and notes.
- **Activity**: something that happened, or needs to happen, with a customer, enquiry or workshop booking. Type (note, call, WhatsApp, email or visit), the record it relates to, a description and when it happened, who logged it, and optionally a callback date, who it's assigned to and whether it's done.
- **Staff member**: a person at the dealership who can be assigned enquiries and callbacks. Name and role. The staff list is managed on one simple settings screen, which also holds the response target (two hours by default).

### Sample data

Accountable comes with realistic South African sample data, so every screen looks alive the first time it starts. All of it is made up; no real person or business appears in it.

- A staff list like the shop's: a dealer principal, three or four salespeople, a workshop manager and someone on tyres.
- Thirty to forty bikes in stock from the premium brands a pre-owned dealer carries (BMW, KTM, Ducati, Triumph, Honda, Yamaha, Kawasaki, CFMOTO), priced from about R40,000 to R320,000. Some are available, some reserved, some sold. A few are listed on only one portal.
- Customers at both statuses, including some who bought a bike here and have since booked it into the workshop.
- Enquiries from every source, at every stage, with enough history for the month-by-month charts to cover the past six months, and the last few weeks at the shop's usual pace. They include enquiries answered quickly, a few still waiting past the response target, sales won and lost over the past months (the lost ones with their reasons), enquiries expected to close in the weeks ahead, and at least one sold bike that still had other open enquiries.
- Workshop bookings across the past and coming week, at every status.
- Activities with some callbacks due today, some upcoming and some overdue.

### Look and feel

The look follows Accountable's brand guidelines, which take priority over any general design guidance. The MVP is light mode, designed for a laptop or desktop screen at a sales desk.

## Affected users and systems

- The sales team and the workshop manager of one small dealership, sharing one computer at the sales desk: a dealer principal, three or four salespeople, a workshop manager and someone on tyres. On a normal day 5 to 15 enquiries come in, 30 or more on a Saturday, and the workshop books in 5 to 10 jobs. There's no sign-in, so whoever logs an activity or takes an enquiry picks their own name from the staff list.
- No other systems are involved yet. Enquiries from AutoTrader, MotoMedia, WhatsApp and social media are entered by hand, or pasted in, when they arrive.

## Constraints

- The technology in `docs/TECH_STACK.md`.
- It runs locally with one documented command that works on Mac, Linux and Windows, and needs no internet connection to use.
- Every change is kept: it's still there after a browser refresh, and every time the app starts it shows every change made before.
- One documented command resets the data to the sample data, to start again from scratch.
- It stays quick with a year's records at the shop's pace: thousands of enquiries and activities.
- Money is in South African rand (R), shown as R 145 000 or similar; dates and times are South African time.
- The response target counts every hour, day and night, not only opening hours.
- Not in the MVP: sign-in, user accounts or permissions; several computers sharing the data; a dark mode or a layout for phones; AI features; pulling enquiries automatically from AutoTrader, MotoMedia, WhatsApp, email or social media; sending messages from inside the app; parts stock, invoicing or job costing; finance applications; reports beyond the dashboard; tags or custom fields; changing the enquiry stages, their probabilities of sale or the workshop statuses; a separate record of each customer's own bikes; archiving records instead of deleting them; importing or exporting data.

## Success criteria

The MVP is built when:

1. Someone non-technical can start Accountable with the one documented command, open it in a browser and land on the dashboard, with sample data on every screen.
2. Customers, bikes, enquiries and workshop bookings can each be added, found by searching, sorted, edited and deleted from their tables, and every change is still there after a refresh and after a restart. Deleting asks first, says how many linked records will go, and then does what it said. The reset command brings back the sample data.
3. Customers can be filtered by status, bikes by status and by "not listed on" a portal, and each record's page shows the records it's linked to, including the bikes a customer owns.
4. An enquiry with no first reply past the response target stands out in the Enquiries table, on its board card and on the dashboard, with how long it has waited. Logging the first contact clears it, records the response time and moves a New enquiry to Contacted. Dragging a New card to Contacted asks for that contact first. Changing the response target on the settings screen changes which enquiries stand out.
5. Moving an enquiry to Sold marks its bike sold, and marking a bike sold on the Stock page asks which enquiry won and moves that one to Sold. Either way, every other open enquiry about that bike gets a callback due today, assigned to its salesperson, and each one shows on the dashboard and in that enquiry's timeline.
6. Dragging an enquiry to another column on the board changes its stage and its probability of sale, and the Enquiries table shows both. A card dropped anywhere in a column, including higher or lower in its own column, stays there after a refresh. The board's and the columns' totals and expected revenue change as soon as the card moves. An enquiry added in a column starts at that stage. Moving an enquiry to Lost asks for a reason. The Sold and Lost columns show only enquiries closed in the last 30 days.
7. An activity or callback logged on a customer, enquiry or workshop booking appears in its timeline, newest first, with who logged it, and so does an entry for each change of stage. Callbacks show on the dashboard as due today, upcoming or overdue until they're marked done. Marking a workshop booking ready for collection creates a "call to collect" callback.
8. A new enquiry can create its customer in the same form, and a mobile number that's already on file is flagged. A lead becomes a customer when one of their enquiries is marked Sold or they get a workshop booking.
9. The dashboard's figures match the data, and they reflect an enquiry marked sold, a first reply logged, or a new callback.
10. Every screen is sharp, modern and professional, and follows the brand. The dashboard is visually stunning, with a line chart, a bar chart and a visual of the pipeline.
11. Before it's called done, someone has used it end to end in a real browser, the way a salesperson and a workshop manager would: every section and every action above, each screen checked by eye, with no errors in the browser's console. Passing tests is necessary, but it isn't enough.

### After a month in use

The checks above say the MVP is built. Whether it works is for the dealership to measure after its first month of real use:

- 90% of enquiries answered within the response target (the dashboard shows this);
- no callback left overdue at closing time;
- every sold bike's other open enquiries called back the same day.

## Open questions

- Pulling enquiries in automatically is the biggest next step: AutoTrader and MotoMedia lead emails, WhatsApp Business and Instagram/Facebook messages landing in Enquiries by themselves. Until then the MVP depends on staff typing each one in, so its real test is whether the team keeps doing that on a busy Saturday.
- Sign-in, several computers sharing the same data (a phone for the salesperson on the floor, a screen in the workshop) and a record of who did what are for a later intent.
- Whether the response target should count only opening hours (a Saturday-evening enquiry answered on Monday morning) needs the dealer's view before it's built. The MVP counts every hour.
- Sending a WhatsApp or email reply from inside the app, with templates for "bike sold" and "ready to collect", is for later.
- Keeping AutoTrader and MotoMedia listings in step with stock automatically is for later; the MVP only shows which portals each bike is on.
- Letting the dealer change each stage's probability of sale, and a proper record of each customer's own bikes with their service history, are for later.

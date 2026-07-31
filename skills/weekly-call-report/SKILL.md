---
name: weekly-call-report
description: >-
  Turns a conversation-analytics API into a short email that a head of sales
  acts on: one headline number, one place where money leaks, one thing to do
  this week. Pulls scores for an account and its reps, finds the largest gap,
  writes the letter in a fixed six-block format, and files it as a task for a
  human to approve before anything reaches the customer. Use for daily, weekly,
  day-0 and follow-up reports.
---

# Weekly call report

A sales leader does not need metrics. They need a verdict: who is losing deals,
where the money leaks, what to do tomorrow. This skill produces that verdict as
an email and stops one step short of sending it.

The report exists because value has to arrive in the inbox. If it waits inside a
dashboard for someone to go looking, most customers never look, and the product
gets judged on a login screen.

## Report types

- `regular` - daily or weekly. The default.
- `day-0` - the first 24 to 48 hours after the customer connects their CRM. It
  proves the system already sees everything, before anyone forms an opinion.
- `follow-up` - the previous letter promised "we will compare these numbers next
  week". Same metric, the delta, and a verdict on whether the fix worked. A
  promise made in an automated email is still a promise.

## Step 1 - Pull the data

The skill needs six things. Names of endpoints will differ per product, the
shape will not.

| What | Why it is needed |
|---|---|
| Account plan and daily usage | Scale line, and a sanity check that data exists at all |
| Users with roles | Recipients are owners and admins. Internal staff addresses are filtered out |
| Scores for the period, by module | The body of the report |
| Scores for the previous identical period | Every number needs a delta, or it means nothing |
| Per-rep call volume, last 30 days | Who to name, and which accounts look broken |
| Daily trends | Weekday gaps, and the "hours of conversation" line |

Then pull per-rep scores for two to four people: the volume leader, the
strongest and the weakest by structure. Names are what makes a sales leader read
to the end. A report without names is a newsletter.

**Trap worth encoding.** An integrations endpoint usually lists only native
connectors. A custom API integration will not appear in it. Absence in that list
is not evidence that the customer has no integration, and writing "connect your
CRM" to someone who already streams calls destroys trust in one sentence. The
signal for a live integration is a steady daily flow, not a lookup table.

## Step 2 - Interpret

Normalize scores to 0-100. Below 40 is a gap and a candidate for "where money
leaks". 40 to 55 is the middle. Above 60 gets praised, explicitly, because a
letter made only of problems does not get opened a second time.

Check in this order, because this is the order in which the findings turn into
money:

1. **Finalization low** - calls end with no next step. Leads go cold and get
   re-dialed, which is the most expensive way to lose a deal twice.
2. **Call purpose low** - the customer never understood why anyone called.
3. **Authority or budget low** - a pipeline of deals that will not close, which
   means the forecast is fiction.
4. **Listen high while assess low** - reps answer the objection without ever
   finding out what caused it.
5. **Engagement low while need alignment high** - a monologue with good content.

## Step 3 - Honesty gates

These are the rules that keep the report credible, and they are the first thing
people cut. Do not cut them.

- **Minimum sample.** Never name a person negatively with fewer than about 20
  scored calls in the period. Below that the number is noise, and naming them
  turns a report into an accusation.
- **Five numbers maximum**, each with a comparison. "6 out of 10" or "the best
  in the team" lands. A bare 47 does not.
- **No module names, no methodology.** The reader does not care what the
  framework is called.
- **The praise block is mandatory**, not decoration.

## Step 4 - The letter, six blocks

1. **Subject is the insight**, never "Report for the 14th". Compare: "611 calls
   checked this week, in 3 out of 4 the customer never heard why you called".
2. **Scale line.** How many calls the system listened to, how many hours that is,
   and how many days of manual work that would have been.
3. **One headline number** out of 100, with the delta against the previous
   period. The delta is the hook that gets the next letter opened.
4. **Where the money leaks.** One anti-insight with the mechanism of the loss.
   Losses move people harder than averages do. Directly beside it, what is
   working.
5. **People.** The strongest and one growth point, one line each, with the cause.
6. **One action for the period.** A ready sentence for the script or a format for
   the Monday stand-up, then the promise to compare the numbers next time. That
   promise is what generates the next report.

**P.S. block.** One or two findings from a standing checklist, which is where
most of the perceived value comes from: shared accounts under one login,
unconfirmed reps whose calls never reach per-person analysis, people with five
calls in 30 days, weekday gaps in the trend line.

**Text rules.** No exclamation marks. No space between a number and the percent
sign. Plain language, calm and partner-like. Body under 200 words. Links as text
anchors, never a bare URL. This is a report to an active customer, so no
unsubscribe footer.

## Step 5 - Send through a human gate

The skill does not send email. It creates a task for the sending agent with the
final body between explicit markers, and a human approves it.

- **Confirm recipients out loud.** Addresses come from the admin API rather than
  from the person asking, so print a "role to address" table and wait for an
  explicit yes before anything leaves the building.
- **There is no post-send correction window.** Once the task exists and its
  deadline arrives, the letter goes. Editing the task afterwards does not catch
  the customer. Everything gets checked before the task is created, not after.
- **Anti-mixup rule for batch runs.** When one endpoint is called for many
  accounts in a single pass, results come back in call order and it is easy to
  shift the account-to-data pairing by one. Tag every result with its account id,
  and re-read the triple "account, headline number, recipients" from the source
  right before creating the task. This rule exists because a real letter once
  went out carrying another account's collapse.

## Step 6 - Write back to memory

After sending, record the task id, the recipients, the period, the headline
metric and its value, which becomes the baseline for the follow-up, and the
promise that was made.

Then schedule the follow-up. A promise to compare numbers is an obligation, and
the calendar is the only place obligations survive.

## What this is not

Not a dashboard, and not a summary of everything the system knows. Each report
exists to produce exactly one decision. If the reader finishes it and has no
obvious next action, the report failed, no matter how accurate it was.

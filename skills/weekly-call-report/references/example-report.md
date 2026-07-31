# Worked example

Synthetic account, invented numbers. The point is the shape, the density and the
order of the blocks, not the values.

Input: account `Northwind Logistics`, interval `last 7 days`, type `regular`.
Previous period headline score: 51.

---

**Subject:** 611 calls checked this week, in 3 out of 4 there was no agreed next
step

Hello Anna,

Over the last seven days the system listened to 611 calls, which is 84 hours of
conversation. Reviewing that by hand is about eleven working days for one
manager.

Overall call quality came out at 47 out of 100, down from 51 the week before.

**Where the money leaks.** In 3 out of 4 calls the conversation ends without an
agreed next step: no date, no owner, no commitment. Those deals do not die, they
go quiet, and the team pays for them a second time in re-dials two weeks later.
This one block is the largest single drop against last week.

**What is working.** Need discovery holds at 68, the strongest part of your
team's conversations, and it went up while everything else went down. The team
finds out what the customer wants. They just leave without agreeing what happens
next.

**People.** Maria leads on volume with 142 calls and also has the best structure
at 61 out of 100, so the volume is not costing her quality. Pavel is the growth
point: 96 calls, and finalization at 38. The pattern in his calls is consistent,
he asks whether the customer has questions and treats "no" as the end.

**One thing for this week.** Add one sentence to the end of the script: "Let us
agree the date right now, I will send the invite while we are still on the
call." Then run next Monday's stand-up on the finalization number rather than on
call counts.

In the next report we will compare that same number and see whether it moved.

Open the workspace

The team

P.S. Two things worth fixing in the account itself. Two people share one login
under a single name, so their calls cannot be separated by person, and four reps
have fewer than five calls in 30 days, which usually means their telephony is
not connected and their conversations are outside the review entirely.

---

## Envelope handed to the sending agent

The skill does not send. It creates a task with the finished body, and a human
approves it before the deadline.

```
Title:     Weekly call report - Northwind Logistics
Deadline:  today, 18:00
To:        anna@example.com (owner)
Cc:        team@example.com
Subject:   611 calls checked this week, in 3 out of 4 there was no agreed next step

===BODY (HTML, send verbatim)===
<p>Hello Anna,</p>
...
===END BODY===
```

The sending agent generates nothing. It sends what is between the markers.
Everything that needed judgement already happened upstream, where it could be
reviewed.

## Memory written after the send

```
account:   Northwind Logistics
task:      #4712
period:    last 7 days
headline:  call quality 47, previous 51
promise:   compare finalization next week
follow-up: scheduled for next Monday
```

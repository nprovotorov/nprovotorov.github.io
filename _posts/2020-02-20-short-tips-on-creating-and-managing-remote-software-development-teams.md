---
title: 'Short Tips on Creating and Managing Remote Software Development Team'
date: '2020-02-20'
categories:
- management
tags:
- "remote work"
- management
---

We will skip the part about why do you do it (remote teams) and get straight to the point. Below are some short tips (derived from my experience, you can agree or disagree with it — it’s OK, this is strictly my opinion) to keep in mind when you are deciding, creating or dealing with remote software development teams.

## My experience in the topic

I have 5+ years of experience working with two remote (aside from HQ) offices (5 to 12 people each) and around 15–20 completely remote workers from different regions and timezones scattered across two countries (~5000km between the most western and eastern employee :P ).

Tips below will work as-is for smaller companies and, I’m sure, will still be mostly valid for much bigger companies.

Not everything on the list we do perfectly and in every team and project, but we are working on it to become better.

## Remote Office setup (ignore this if you are hiring remote workers without the office)

Here are some points to remember if you are going to open a new Remote Office:

- **Geography** — choose it wisely. You should know in advance who are your candidates, how many there are, where will they come from, how you will attract them, how will you keep them, who are your competitors on this market and so on. Apart from this, you should spend some time thinking about logistics (sending documents, buying/repairing equipment, furniture, etc.)
- **Conference** rooms — you need them. At least one. They work for big meetings and private matters. Of course, you will need a whiteboard (more is better), TV, camera and speakerphone there.
- **Trusted leader** — you could do without him, but with him, it would be 10 times easier, faster and better. It would be best if he shares your core values and principles and worked with you in HQ for some time (to share your culture and be able to spread it in the new office).
- **Periodic Top-management visits** — Again, you could live without it, but these visits serve two things: 1) they show your employees that they really matter and top-management knows and cares about them 2) gives top-management first-hand information about how are things really going “on the ground”.
- **Team purchase** — you should consider purchasing a ready-made team (at least 3 people) on the market and opening a new office on their base. This will speed up things, but it also can complicate culture integration and communications (if this team will try to isolate itself, and most teams will).

## Hiring

Precise hiring becomes much more important with remote workers as you could not see a miss as soon as you could do it if a person is sitting near you.

- **Interview with Team Lead and/or Manager** — this is a must. You should check the “compatibility” of a new developer with his Team Lead and/or manager. Don’t hire if TL says that this was a good guy/girl and we should hire him, but “not in my team”.
- **Interview with the camera** — you could skip it, but it makes things much easier. Non-verbal signals are important and you should try to see your candidates in live conversation before you hire someone.
- **Previous experience in remote work** — it would be best if a candidate has already worked remotely. Not everyone can work like this.
- **Timezones** — you should choose what timezones are acceptable for you. We are most comfortable with ±2 (and ±4 max) hours from HQ time, but it could differ greatly depending on your specifics. You should be clear on this topic in the interview.
- **Region specifics** — some regions have their own working culture that will influence a candidate’s performance — in some regions, there are mostly fast and furious candidates and in some are mostly slow and meditative candidates, the same picture with reliability, etc. From experience, we have calculated some regions where we try to avoid hiring people.
- **Region hiring specifics** — e.g. in some regions there is no “open” market for developers — they choose a new company completely by word of mouth, or based on where they relatives or friends work and so on, so you can’t use hiring sites or ads there. This specifics could render useless your hiring strategy — so keep it in mind.
- **Check core values** — very important. You should check every candidate (local or remote) if their core values are aligned with yours, but with remote workers, you should double-check it.
- **Good communication skills** — very important. Both written and spoken. Twice as important as for the local staff.
- **Finally — Don’t hire if you are not sure** (this tip becomes less relevant for big companies as they can live through this kind of errors with much less damage, but for small companies, it can be deadly).

## Onboarding

You should learn how to onboard new employees fast, efficient and with the predictable result.

- **Onboarding process** — you should have one. It could be short and simple or it could be a boot camp in the jungle, but it should be in place. Every new employee should go through it.
- **Mentor** — a must. You should assign a mentor for every new employee, that will supervise and advise a newcomer in the first few months (in our case mentors are mostly Team Leads).
- **Formal Probation expectation** — very important. For every role you hire, you should have some template with formal expectations from the person during the Probation period (like what he should know, do/not do, demonstrate, deliver, etc. at the end of the Probation). You should tailor it to the concrete employee and have regular talks with them on their progress in achieving these expectations. Mentors should lead this.
- **Local assimilation** — ideally if newcomers can work for some time (first weeks, better months) in HQ to make connections and soak up your culture. Not always possible, but worth it.

## Infrastructure

- **Remote access to infrastructure, services, environments, etc.** — no access, no work :) You should be ready for it with some typical procedures to grant required access for newcomers (VPN, accounts, roles, permissions and so on).
- **Information security** — with remote workers the attack surface becomes much higher — you should think about how you will protect and audit your data, services, etc.

## Tools and Software

- **Software licences** — Don’t forget you need them. If they don’t sit in your office doesn’t mean that they don’t use your software licences (e.g. IntelliJ IDEA, MS Visual Studio).
- **Issue tracking software** — a must-have. Jira, TFS, Trello — any will do, but you should have one. And only one.
- **Code versioning systems** — a must-have. Git, SVN, etc. will do. But the most common CVS nowadays is Git, so just use it if you don’t have any special reasons not to.

## Management

- **Highly skilled and communicative Team Leads that actually Care for their teammates** — this is a key factor for success. Try to find them or grow them.
- **Balanced team compositions** — like 1xSenior-2xMiddle-3xJunior, and not 1xMiddle-5xJunior. Try not to build entire teams from scratch (not always possible) — build a new team on the base of a current employee, who already holds culture and knowledge and share it with newcomers.
- **Clear expectations** — always translate clear expectations of people, tasks, etc.
- **Just enough standards and processes** — don’t push too much, but don’t leave too much at chance either. Planning, Code conventions, Branching, Pipelines, Rules on working with Issues, Release management — mostly must-have formal processes.
- **Daily meetings (e.g. SCRUMS)** — absolutely mandatory. Just use it.
- **Retrospectives** — learn how to do good ones. Almost must-have for remote teams.
- **Good requirements** — depends on your business, but most of the time you should put all of the effort to get the best and detailed requirements you can as remote communications are much less efficient and many things could be understood incorrectly. You really should pay attention to this.
- **Use Issue tracker for all of your work** — no comments. Just use it.
- **Excessive control at the start** — controversial topic, but try it. Synchronize on goals at the start of the day, check progress in the middle, check results at the end. If it is going well — relax and gracefully stop it, if it is not going well — make corrections.
- **Metrics** — have some metrics and watch for them regularly (e.g. velocity, bugs per feature, etc.). This will help you measure the performance of individuals and teams and look for problems. But be accurate with metrics, they should not become KPIs so people will not start to abuse them.

## Communications and Knowledge Sharing

- **Architecture diagrams** — you should have at least High Level Design diagrams and everyone should know where to find them.
- **Wiki** — an absolute must — this is an external brain for your company. Any will do, but Confluence is the most popular choice. You should pay special attention to make everyone contribute to wiki articles and not hold information in emails, brains, napkins, etc.
- **Chat** — controversial thing. But better have some structured chats with dedicated channels. Most popular are Slack, MS Teams, Skype. Use very carefully because chats can steal a lot (surprisingly a lot) of productive time from the teams.
- **Feedback on communications** — you should give it to each other regularly. Always try to improve it — become more clear, gentle, efficient.
- **Overcommunicate** — always. Not sure? Overcommunicate. Sure? Same.
- **1 on 1 s** — you should be doing them. Your Team Leads and managers should be doing them too. No excuses. They could be short and simple, but they must be in place.

## Developing people

- **Individual Development plans** — talk with people, get to know what are they interested in, make formal IDPs, attach mentor, regularly track progress — PROFIT.

# Culture

- **A formal manifestation of your core values and principles incorporated in culture** — a very hard thing to do, but can help tremendously.
- **Culture agents/evangelists** — ideally if you have at least one in every team. They should “infect” their teammates with your culture (but reverse effect could also happen).
- **The Gathering** — you should try at all costs to gather all of your remote workers in one place at least several times a year (for example, on corporate events, strategy sessions, etc.).

That’s it. And may the Force be with you.

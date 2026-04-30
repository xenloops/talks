Title
# Why People Hate App Sec
...and the Tools They Ride In On



# About the speaker
Blah blah blah
Contact info

# The Build is Broken
...and it's not the scanner's fault

Let's begin with a story...

Security wants fewer risks. Devs want fewer blockers. Why are these treated as opposites?


# Why Devs Push Back (10)
...or totally blow AppSec off

* Too many tools! -- One for defects in custom code, one for defects in third-party libraries, one for hard-coded secrets getting checked in (only one each if lucky -- what happens when one dept installs SonarQube?). Forget about adding Yet Another Tool! That brings with it pleadings, then mandates, then trainings, then metrics, then leadership attention.
* Notification fatigue -- Every finding is an alert
* Backlog fatigue -- When is every finding the tool injects supposed to be remediated, with all these other priorities?
* Meeting fatigue -- Between standups, sprint planning, sprint refinement, retrospectives, PI pre-planning, PI planning.... do you really want to call them into another meeting about one part of the job?

## The Psychology of Security Friction

* Incentive misalignment -- Devs are measured on velocity and features shipped, by the sprint. Security debt is invisible until it isn't. Nobody gets a bonus for a CVE they prevented. (Dilbert strip with Wally "writing himself an RV")
* The "gate" mental model -- Security as a checkpoint at the end of the SDLC trains devs to see it as a last-minute tax, not a design input.
* Alert fatigue and tool noise -- when everything is P1, nothing is. We've all heard complaints about false positives from SAST tools. Tools that produce too much noise get ignored. Tuning tool output or focusing on the risk important to the business is essential! Can't catch 'em all.
* The vocabulary gap -- AppSec speaks in CVSS, CWE, and TTF; devs speak in sprint velocity and backlog debt. Mutually unintelligible.
* The BISS Model -- AppSec says "do it Because I Said So", devs really need to know how big a risk the defect is.

Quick poll: How many have had a security finding closed -- or closed one -- as "won't fix" with no conversation?


# What's at Stake (5)
Framing Risk in Terms Development Leads Care About

* The threat landscape shifts faster than SDLCs -- were designed for. This is the argument for shifting left.
* Regulatory and liability pressure is increasing -- PCI-DSS, SOC 2, CISA, litigious customers, etc.
* Cost of late-cycle remediation vs. early-cycle (but... [1]) -- Concrete, well-known, leadership-friendly argument (IBM/NIST data on cost-to-fix by phase)
* Key reframe: it's not AppSec's problem -- But AppSec was formed to own the engineering quality control problem


# The Pipeline is Your Friend (15)

What "integrated" really means vs. what it usually looks like in practice (bolted-on vs. baked-in)

## Maturity levels (informally):

1. "We pass zip files around." -- Sneakernet
1. "We check the code out when someone's working on it, and that blocks others from changing it." -- TFS way?
1. "We're fully GIT-ified, but what's this I hear about secure code?"
1. "Scanning happens before pushing to Prod; we have a TTF policy based on severity."
1. "Scanning happens before pushing to Prod, and blocks the build." -- This by now should be a legacy model. 
1. "We do pre-commit checks for all security tests." -- Better...
1. "All our tools are in the devs' IDEs." -- All of the tools you use should have IDE plugins that scan automatically -- think like a spell-checker for code. Allows devs to fix potential defects while what they wrote is still fresh in mind, not from three PIs ago. Convincing devs of this may take effort! Some really don't like other teams messing in their dev tools.
1. "Tools in the IDE flag findings _and_ recommend fixes in context." -- This is state-of-the-art. As long as the LLM-generated suggestions are good ones.

## Principles for low-friction tooling

* Surface findings where developers work -- IDE plugins, PR comments, not a separate portal
* Signal-to-noise tuning -- Suppress accepted risks so new findings land with impact.
* Work with the business -- Flag the findings that business cares about. If Criticals and Highs are the only findings that business wants resolved, don't even show Mediums and lower to the devs.
* Actionable output -- Not just "it's vulnerable" but "here's a fix, here's why it matters, here's the blast radius"
* Convince dev teams that it's in their best interest. -- Do you want to know of and fix an issue locally, or wait until it blocks you and your PM schedules a meeting with security?
* Be reasonable -- Not every security check belongs in pre-commit or the IDE. Secrets, SAST (at least for criticals), yes; pen-testing or DAST takes longer, and SCA results usually don't change frequently. How about developer security training in the workflow?

[Concrete tool-agnostic example: what a well-integrated SAST/SCA setup looks like in a CI/CD pipeline]

# Bridging AppSec, Engineering, and Leadership (10)

How to speak with...

* **Developers** Lead with empathy, not compliance. -- "Here's what this would cost you if it hits prod (time, missed features, meetings)" beats "the policy requires this."
* **Engineering leads** Translate risk into delivery risk. -- Unpatched vulnerabilities are technical debt with an unpredictable interest rate.
* **Leadership** Connect scanning to business outcomes -- Liability, brand, customer trust, regulatory posture. Avoid security theater or FOGH (Fear of Getting Hit); propose measurable outcomes.

Ideas

* Introduce a lightweight Friction Audit concept -- A quick internal exercise teams can run to identify where AppSec is creating the most drag and why (they'll probably have a list already).
* The security champion model as a cultural bridge -- Embedding security-minded devs in teams (or training the devs with interest in security) rather than relying solely on a central AppSec Dept.
* Leaderboards (wihtout metrics) -- Show the ranking of dev teams working closest with security, by e.g. proportion of repos orchestrated, number of security trainings completed, proportion of findings resolved before prod, etc.

# A Pragmatic Framework (5)

AppSec as an Enabler: A Model You Can Take Back Next Week

| Layer | Activity |
|--|--|
| People/Culture | Shift the narrative from "security says no" to "security helps us ship confidently". |
| Process | Define clear ownership. Not every security decision belongs to AppSec. |
| Tools | Integrate findings into developer workflows; tune the noise out! |


# Adaptation as the Core Skill (5)

The orgs that adapt fastest aren't the ones with the most tools — they're the ones that removed the organizational friction preventing good security hygiene

Concrete conversation starters to use next week

The goal isn't a frictionless AppSec program. It's friction in the right places — and acceleration everywhere else.



# Misc notes


# Development pressures
### (What's the big deal?)

Developers have enough:

* Notifications
* Meetings
* Tasks

# YAT

Adding another tool offers devs:

* AuthN / authZ headaches
* Another source of support calls
* Another time-sucking UI to navigate

# How do we try to help?

* Tool integration
* Trainings
* Metrics

# But...

* Tool integration -- some installation required
* Trainings -- great, another time-suck
* Metrics -- yet another dimension in which to be judged




# Sources
[1] T. Anderson, "Everyone cites that 'bugs are 100x more expensive to fix in production' research, but the study might not even exist," The Register, Jul. 22, 2021. [Online]. Available: https://www.theregister.com/2021/07/22/bugs_expense_bs. [Accessed: Apr. 23, 2026].


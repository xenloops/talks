```v20260507.1```

Title slide
# Why People Hate App Sec
...and the Tools They Ride In On



# About the speaker
Blah blah blah
Contact info


# Premise

To devs, AppSec can come across less like a partner and more like a Vogon:
"Not actually evil, but bad-tempered, bureaucratic, officious and callous."


D. Adams, _The Hitchhiker's Guide to the Galaxy_. London: Pan Books, 1979.

["Resistance is useless!" scene from TV show]

# The Build is Broken
...and it's not the scanner's fault

Let's begin with a story...

Security wants fewer risks. Devs want fewer blockers. Why are these treated as opposites?


# Why Devs Push Back (10)
...or totally blow AppSec off

* Too many tools! -- One for defects in custom code, one for defects in third-party libraries, one for hard-coded secrets getting checked in (only one each if lucky -- what happens when one dept installs SonarQube?). Forget about adding Yet Another Tool! That brings with it pleadings, then mandates, then trainings, then metrics, then leadership attention. Adding another tool offers IAM headaches, another source of support calls, another time-sucking UI to navigate.
* Notification fatigue -- Every finding is an alert!
* Backlog fatigue -- When is every finding the tool injects supposed to be remediated, with all these other priorities?
* Meeting fatigue -- Between standups, sprint planning, sprint refinement, retrospectives, PI pre-planning, PI planning.... This is peak Vogon bureaucracy! Do you really want to call them into another meeting about one part of their job?

# Face it, developers have enough:

* Notifications
* Meetings
* Tasks
* Nags

# How do we try to help but utterly fail?

* Tool integration -- some assembly required, probably with fun authentication tweaking involved and occasional IDE crashes.
* Trainings -- great, another time-suck, especially when it's the same OWASP Top 10 module they took in 2019.
* Metrics -- let's embarrass dev teams for using 150 slightly outdated libraries, but ignore the fact that they're working with their security champion, coming to AppSec office hours with questions, and lost half their staff in the last RIF.

## The Psychology of Security Friction [separate slides?]

* Incentive misalignment -- Devs are measured on velocity and features shipped, by the sprint. Security debt is invisible until it isn't. Nobody gets a bonus for a CVE they prevented. (Dilbert strip with Wally "writing himself an RV")
* The "gate" mental model -- More Vogon behavior. Security as a checkpoint at the end of the SDLC trains devs to see it as a last-minute tax, not a design input.
* Alert fatigue and tool noise -- when everything is P1, nothing is. We've all heard complaints about false positives from SAST tools. Tools that produce too much noise get ignored. Tuning tool output or focusing on the risk important to the business is essential! Can't catch 'em all.
* The vocabulary gap -- AppSec speaks in CVSS, CWE, and time-to-fix; devs speak in sprint velocity and backlog debt. Mutually unintelligible.
* The BISS Model -- AppSec says "do it Because I Said So", devs really need to know how big a risk the defect is [a real and common failure mode worth naming].

Quick poll: How many have had a security finding closed -- or closed one -- as "won't fix" with no conversation?


# What's at Stake (5)
Framing Risk in Terms Development Leads Care About

* The threat landscape shifts faster than SDLCs were designed for -- This is the argument for shifting left.
* Regulatory and liability pressure is increasing -- PCI-DSS, SOC 2, CISA, litigious customers, etc.
* Cost of late-cycle remediation vs. early-cycle * -- Concrete, well-known, leadership-friendly argument: Famous IBM/NIST study on cost-to-fix by phase (although it might be fabricated, it makes a good point).
* Key reframe: it's not AppSec's problem -- But AppSec was formed to own the engineering quality control problem

* T. Anderson, "Everyone cites that 'bugs are 100x more expensive to fix in production' research, but the study might not even exist," The Register, Jul. 22, 2021. [Online]. Available: https://www.theregister.com/2021/07/22/bugs_expense_bs. [Accessed: Apr. 23, 2026].

# The Pipeline is Your Friend (15)

What "integrated" really means vs. what it usually looks like in practice (bolted-on vs. baked-in)

## Maturity levels (informally) -- Survey: where does your org sit?

0. "We pass zip files around." -- Sneakernet
1. "We use git, but no security." -- No scanning in the pipeline, maybe even no PR approvals. Right to prod.
2. "Scanning happens before pushing to Prod; we have a time-to-fix policy based on severity."
3. "Scanning happens before pushing to Prod, and blocks the build."
4. "We do pre-commit checks for all security tests."
5. "All our tools are in the devs' IDEs." -- The tools you use have IDE plugins that scan automatically; think like a spell-checker for code. The tools might even recommend fixes in context. Allows devs to fix potential defects while what they wrote is still fresh in mind, not from three PIs ago. Convincing devs of this may take effort! Some really don't like other teams messing in their dev tools.

## Principles for low-friction tooling

Some distinctly anti-Vogon ideals:

* Surface findings where developers work -- IDE plugins, PR comments, not a separate portal
* Signal-to-noise tuning -- Suppress accepted risks so new findings land with impact.
* Work with the business -- Flag the findings that business cares about. If Criticals and Highs are the only findings that business wants resolved, don't even show Mediums and lower to the devs. 
* Actionable output -- Not just "it's vulnerable" but "here's a fix, here's why it matters, here's the blast radius"
* Convince dev teams that it's in their best interest. -- Do you want to know of and fix an issue locally, or wait until it blocks you and your PM schedules a meeting with security?
* Be reasonable -- Not every security check belongs in pre-commit or the IDE. Secrets, SAST (at least for criticals), yes; pen-testing or DAST takes longer, and SCA results usually don't change frequently. How about developer security training in the workflow?

## Enshiftifying the SDLC

Yes, shift left, but don't throw everything into pre-commit. The scans that belong there are:

* Quick -- e.g. 5 seconds or less
* Low false-positives -- so not SAST?
* Actionable immediately -- no need for back-and-forth with security

Good candidates:

* Secret scanning
* Highly focused, lightweight SAST -- put the riskiest, highest confidence rules here
* IaC linting -- limited ruleset of course

[Concrete tool-agnostic example: what a well-integrated SAST/SCA setup looks like in a CI/CD pipeline]

# Bridging AppSec, Engineering, and Leadership (10)

How to speak with...

* **Developers:** Lead with empathy, not compliance. -- "Here's what this would cost you if it hits prod (time, missed features, meetings)" beats "the policy requires this." In short, don't be a Vogon.
* **Engineering leads:** Translate risk into delivery risk. -- Unpatched vulnerabilities are technical debt with an unpredictable interest rate.
* **Leadership:** Connect scanning to business outcomes -- Liability, brand, customer trust, regulatory posture. Avoid security theater or fearmongering; propose measurable outcomes.

Ideas

* Introduce a lightweight Friction Audit concept -- A quick internal exercise teams can run to identify where AppSec is creating the most drag and why (they'll probably have a list already).
* The security champion model as a cultural bridge -- Embedding security-minded devs in teams (or training the devs with interest in security) rather than relying solely on a central AppSec Dept.
* Recognition-first metrics -- Show the ranking of dev teams working closest with security, by e.g. proportion of repos orchestrated, number of security trainings completed, proportion of findings resolved before prod, etc. These are metrics that reward overall progress, not perfection.

# A Pragmatic Framework (5)

AppSec as an Enabler: A Model You Can Take Back Next Week

| Layer | Activity |
|--|--|
| People/Culture | Shift the narrative from "security says no" to "security helps us ship confidently". |
| Process | Define clear ownership. Not every security decision belongs to AppSec. |
| Tools | Integrate findings into developer workflows; tune the noise out! |


# Adaptation as the Core Skill (5)

The orgs that adapt fastest aren't the ones with the most tools — they're the ones that removed the organizational friction preventing good security hygiene

# Concrete conversation starters to use next week

* With developers: What's your biggest beef with the security tools we use here, or in the way we use them? -- Shows Security is willing to listen to the people who potentially generate risk, and adapt.
* With engineering leads: Let's spend 20 minutes mapping which security issues are actual delivery risk. -- Reframes security as a sprint planning input, not an audit. The 20-minute constraint signals respect for their time.
* 

# Conclusion

The goal isn't a frictionless AppSec program. It's friction in the right places, and acceleration everywhere else. In other words, an AppSec program that doesn't read like Vogon poetry.



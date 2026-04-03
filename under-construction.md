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

## The Psychology and Dynamics of Security Friction

* Incentive misalignment — devs are measured on velocity and features shipped, by the sprint. Security debt is invisible until it isn't. Nobody gets a bonus for a CVE they prevented. (OK to show Dilbert strip now, with Wally "writing himself an RV"?)
* The "gate" mental model — security as a checkpoint at the end of the SDLC trains devs to see it as a last-minute tax, not a design input.
* Alert fatigue and tool noise — when everything is P1, nothing is. SAST/DAST/SCA tools that produce undifferentiated noise get ignored.
* The vocabulary gap — AppSec speaks in CVSS scores and CWE IDs; devs speak in sprint velocity and backlog debt. Same problem, mutually unintelligible.

Quick poll: How many have had a security finding closed as "won't fix" with no conversation?


# What's Actually at Stake (5)
Framing Risk in Terms Engineering Leads Care About

* The threat landscape moves faster than most SDLC processes were designed for (the actual argument for shifting left)
* Regulatory and liability pressure is increasing (relevant guidance - PCI-DSS, SOC 2, CISA, etc.)
* The cost of late-cycle remediation vs. early-cycle is a concrete, leadership-friendly argument (IBM/NIST data on cost-to-fix by phase)
* Key reframe: this isn't AppSec's problem — it's an engineering quality problem that AppSec has been asked to own

# The Pipeline is Your Friend (15)

What "integrated" really means vs. what it usually looks like in practice (bolted-on vs. baked-in)

Principles for low-friction tooling:

* Surface findings where developers work (IDE plugins, PR comments, not a separate portal)
* Signal-to-noise tuning — suppress known/accepted risks so new findings land with impact
* Actionable output: not just "it's vulnerable" but "here's a fix, here's why it matters, here's the blast radius"

Shift-left without shift-all — not every security check belongs in pre-commit. Know what belongs where in the pipeline.
Concrete tool-agnostic example: what a well-integrated SAST/SCA setup looks like in a CI/CD pipeline
Emerging approaches: AI-assisted remediation suggestions, policy-as-code, developer security training embedded in workflow

# Bridging AppSec, Engineering, and Leadership (10)

With developers: Lead with empathy, not compliance. "Here's what this would cost you if it hits prod" beats "the policy requires this."
With engineering leads: Translate risk into delivery risk. Unpatched vulnerabilities are technical debt with an unpredictable interest rate.
With leadership: Connect to business outcomes — liability, brand, customer trust, regulatory posture. Avoid security theater; propose measurable outcomes.
Introduce a lightweight Friction Audit concept: a quick internal exercise teams can run to identify where AppSec is creating the most drag and why
The "security champion" model as a cultural bridge — embedding security-minded devs in teams rather than relying solely on a central AppSec function

# A Pragmatic Framework (5)
AppSec as an Enabler: A Model You Can Take Back Next Week


Layer - What to do
People/Culture - Shift the narrative from "security says no" to "security helps us ship confidently"
Process - Define clear ownership — not every security decision belongs to AppSec
Tools - Integrate findings into developer workflows; tune noise ruthlessly



# Adaptation as the Core Skill (5)

The orgs that adapt fastest aren't the ones with the most tools — they're the ones that removed the organizational friction preventing good security hygiene

Concrete conversation starters to use next week

The goal isn't a frictionless AppSec program. It's friction in the right places — and acceleration everywhere else.



# Misc notes

# The BISS Model

# The YAT Effect

Developers hear that Security is:

* Installing Yet Another Tool*
* Mandating the tool
* Offering trainings

*That development didn't ask for

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

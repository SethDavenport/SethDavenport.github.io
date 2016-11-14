class: divider, middle

.center[
  # Automatic Agile
  ### The Value of Continuous Delivery
]

.bottom[
** Yuri Takhteyev **

* CTO, Rangle.io
* yuri@rangle.io

** Seth Davenport **

* Software Architect, Rangle.io
* seth@rangle.io
]

---

## Session Intro

#### Talking About a Software Project is Hard

* Software is complex
* Team dynamics are complex
* Business problems are complex
* Cross-functional teams have multiple spheres of knowledge

  * Business objectives
  * Technical considerations
  * Branding concerns
  * Legal and regulatory concerns

--
count: false
* 'Is this feature done?' can be unnecessarily hard to answer.

---

### Improving the Conversation

The only meaningful way to understand the state of the project is through actual, working software.

> "Working software over comprehensive documentation"
--
count: false

Running software should be:
--
count: false

* Visible to every one on the team
--
count: false
* Always available and up-to-date
--
count: false
* A project's _single source of truth_.

If you don't have running software, **no amount of checklists or 'definitions of done' will help.**

---

class: center, middle

> Continuous delivery is a set of practices that allow each code change
to be deployed to a staging system automatically.
--
count: false

It's _how we ensure we have working software at all times_.
--
count: false

It's how we make the project status conversation _possible_

---

class: middle, divider

# Breakout Discussion

* When have you thought your project was making progress only to find that it wasn't working at all?

* Cases where talking failed you:
  * Everyone talked about progress
  * It sounded like things were working, but then they weren’t.

---

class: middle, divider

# Group Discussion: Why does this happen?

* Why is there so much misunderstanding about what’s been done.
* Why doesn’t “definition of done” save us?

---

### Running Software: the Single Source of Truth

--
count: false
Our daily conversations are consistently backed by a 'project source of truth' deployment

--
count: false
* It runs in an 'official place'
--
count: false
* It can be accessed all by stakeholders at any time
--
count: false
* Demos happen exclusively from this system
--
count: false
  * _never from developer machines!_
--
count: false
  * avoids 'smoke and mirrors' demos

---

## Keeping it "True"

Attributes that make this system accurately reflect the project:

--
count: false
* It's always working
--
count: false
* It's always up-to-date with the codebase.


--
count: false
* **We are automating the "definition of done".**
--
count: false
  * A feature is done if a stakeholder can use it.

---

## Challenges...

--
count: false
### ... making it official

--
count: false
* Entails changes to the ways teams work
--
count: false
* Provides radical visibility: organizational discomfort
--
count: false
* Initial setup can take extra resources

--
count: false
### ... setting it up

--
count: false
* Puts demands on IT and devOps personnel
--
count: false
* Facilitated by modern cloud IT
--
count: false
  * Traditional IT approaches may struggle initially

--
count: false
### ... keeping it technically accurate

--
count: false
* Automate, Automate, Automate
--
count: false
* Keeping quality high

---

class: middle, center, divider

# Activity: What challenges do you anticipate in your organization?

---

class: middle, center

# Continuous Delivery at Rangle
_A case study_

---

# The 'Keep it Working' Mentality

--
count: false
- A project with broken code provides no value
--
count: false
- Broken code === broken project
--
count: false
- Each work unit submitted to the system undergoes 'pipeline' of quality checks
--
count: false
- If the PSOT system breaks, fixing it is the team's first priority.

---

# The Quality pipeline

.diagram[![](TAC-2016/pipeline.svg)]

---

## Automate, Automate, Automate

* Automation saves the team time
--
count: false
* It reduces manual errors
--
count: false
* Use it to deploy to the PSOT system whenever work items are merged
--
count: false
* Use it to run automated quality checks on each work item

--
count: false
Used correctly, it keeps the source of truth both up and 'true'

---

## Making it Work: Technical Ingredients

* A central source code repository
--
count: false
  * GitHub or BitBucket
--
count: false
* Machines to run code on
--
count: false
* Elastic provisioning
--
count: false
  * Heroku
  * AWS EC2
--
count: false
* A way to run automation scripts by listening to changes to the repo
--
count: false
  * CircleCI
--
count: false
* A way to get code onto the boxes.
  * Heroku tools
  * In-house scripts
---

## Making it Work: Process Ingredients

* Small, focused stories
--
count: false
* Trunk based development with feature branches
--
count: false
* Limiting work in progress
--
count: false
* vertical integration of each work unit.
---

## CD to Production: When and How?
--
count: false
* Once we have a project source of truth, can we push this further?
--
count: false
* Not just continuous deployment internally, but to production as well?
--
count: false
* How confident are you in your Quality Pipeline?
--
count: false
* Pulling it off can take you from Agile to Lean

---

class: middle, center, divider

# Activity: Group discussions

---

class: middle, center

# Continuous Deployment in the Enterprise
_A playbook_

---

## Recap: Technical Ingredients for an Ideal Setup

* A central source code repository
  * GitHub or BitBucket
* Machines to run code on
  * Elastic provisioning
  * Heroku
  * AWS EC2
* A way to run automation scripts by listening to changes to the repo
  * CircleCI
* A way to get code onto the boxes.
  * Heroku tools
  * In-house scripts

---

## Enter the Enterprise

* In the Enterprise, some or all of these ingredients may be missing!
--
count:false
* Other constraints may complicate access:
--
count:false
  * VPNs preventing stakeholders from seeing the system
--
count:false
  * Difficulty deploying to Mobile devices.
--
count:false
* These constraints affect our ability to automate the quality pipeline.

---

### Recap: the Quality Pipeline: What can we Live Without?

---

### Playbook: Source Code Repo Behind Internal Firewall

#### Constraint:

* Can't use cloud automation tools like CircleCI, TravisCI, etc.

#### Play:

* Fall back to internally hosted solutions instead (e.g. Jenkins)

---

### Playbook: Source Code Repo Behind Internal Firewall

#### Pros:

* Very flexible
* Can work in completely firewalled environments
* No public access to the internet required.

#### Cons:

* Much more work to set up
* Need to manage a CI server yourself - needs collaboration with IT
* Solutions like Jenkins tend to require a lot of manual scriptwriting.

#### Mitigation:

* Your team will need a stronger devops developer.

---

### Playbook: Waterfall Approach to Quality Assurance

> "We'll have our outsourced QA team to all the testing at the end. What could
  possibly go wrong?"

#### Constraint:

* Lack of testers tightly integrated with the dev team results in a PSOT that's broken for a significant percentage of the time.
* Broken Code === Project with no value
* We get nasty surprises at the end: state of project is no longer clear.

#### Play:

* Dedicate one developer to automated regression tests
  * Tools like selenium etc. that drive the browser or the app as a user would.

---

### Playbook: Waterfall Approach to Quality Assurance

#### Pros:

* Ongoing, per-story testing happens as part of the quality pipeline

#### Cons:

* Can be costly in terms of developer time
* Hard to know what the right level of automated testing is.

---

### Playbook: Inelastic Provisioning

> "I can't use cloud providers with elastic provisioning; instead I'm stuck with
some machines in a closet managed by an unresponsive IT department."

#### Constraint:

* Provisioning and teardown of machines up and down can't be automated.

#### Play:

* Just automate PSOT deployments
* Review apps are not possible in this environment.

---

### Playbook: Inelastic Provisioning

#### Pros:

* We still have our source of truth system constantly up-to-date.
* This is most of the value of CD

#### Cons:

* Manual QA can no longer be performed _prior_ to merging a work unit.
* Must happen on the PSOT system itself
* Expect more bugs to reach the PSOT system.

#### Mitigation:

* A stronger emphasis on automated testing
* stricter code reviews
* budget for remediation time when the PSOT is affected.

---

### Q & A

* What constraints/resistance have you faced?
* How have to worked around them?

---

class: middle, center, divider

# Topical Discussions: Mini Open-Space

---

class: middle, center, divider

# Q & A

---

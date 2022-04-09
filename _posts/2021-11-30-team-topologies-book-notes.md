---
title: 'Notes on Team Topologies Book'
date: '2021-11-30'
categories:
- Management
- Books
tags:
- Management
- Teams
- Books
---

![cover](/assets/images/2021-11-30-team-topologies-book-notes/book_cover.jpg)

## General notes

Overall this is a great book, and many other authors and sources recommend it as a must-read for any management role.

I will recommend it as well 🙂 This book gives a good structure on how to think and design your teams.

But... it could be like 3x times shorter than it is right now. A big part of the text is just a repetition of what was already said, just from a different angle.

## Some of my notes

Book methodology relies heavily on [Convey's Law](https://en.wikipedia.org/wiki/Conway%27s_law) and respective `Reverse Convey Maneuver` (when we design team structures to match the desired architecture)

> Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure.
>
> — Melvin E. Conway

## Management principles

- Teams are fundamental building blocks for organisational design
- Teams should be five to nine people
- Teams should "own" their software
- Each part of the system needs to be owned by exactly one team (no shared ownership)
- Move authority to leaders with the best information to take action (move away from Command and Control structures)
- Organization Design should go hand in hand with System Design - they are connected and influence each other
- Manage cognitive load on teams (clear teams responsibilities and boundaries)
- Organization should not allow any subsystem to grow beyond the cognitive load of its team (match software boundaries to team cognitive load)
- Teams should be long-lived and autonomous
- Work should go to the Team not the other way around
- Software architecture is needed before we organize teams, otherwise, team structure will dictate the architecture
- Use proven software architecture good practices to achieve fast flow within teams:
  - Loose coupling
  - High cohesion
  - Version compatibility
  - Cross-team testing
- Fast flow requires restricting communication between teams (not in every case - where we need to explore something and find a new knowledge communication is encouraged, but where we need execution - communications should be kept to a minimum)
- Architects need to be a manager too (or managers will be your architects)
- If two teams that should not be communicating heavily according to bad designs in fact ARE communicating heavily - something is not right (API issues, platform issues, etc.)
- Some people just can't work in teams - remove them
- Reward whole teams, not individuals
- Minimize team distractions (limit meetings, reduce emails, etc.)
- Increase Developer Experience for other teams who are using your code or API
- Define Team APIs (code, documentation, UX, etc.)
- Use business domain bounded contexts to define software (and team) boundaries
- Reduce handover between teams
- Delivery teams should be cross-functional, with all the skills to design, develop, test, deploy and operate the system
- Feature teams require high engineering maturity (automating tests, minimal dependencies, CI/CD, etc.)
- Change team topologies and team interactions according to your situation (they should not be static)

## Team Types according to Team Topologies authors

![team types](/assets/images/2021-11-30-team-topologies-book-notes/team_types.png)

#### Stream aligned teams

- primary team form - most teams should be of this type, all other types exist to support it
- aligned to a single valuable stream of work
- able to build and deliver customer value quickly, safely, without requiring hand-offs to other teams
- optimized for flow
- use loose coupling, minimize dependencies and coordination between Stream-aligned teams
- use Complicated-subsystem teams and Platform teams to reduce cognitive load

#### Enabling team

- collaborative nature
- "Technical Consulting Teams"
- provides guidance, not execution
- End goal: increase the autonomy of stream-aligned teams by growing their capabilities. Stream-aligned team should not have a need for enabling's team help after a few weeks or months

#### Complicated-subsystem team

- build and maintain part of the system requiring heavily specialist knowledge

#### Platform team

- enable stream-aligned teams to deliver work with autonomy
- provides internal services to reduce the cognitive load of stream-aligned teams
- strong focus on usability and reliability for their services
- aim for the thinnest viable platform (TVP) and avoid letting the platform dominate the discourse
- should focus on Developer Experience

## Team Interaction Modes according to Team Topologies authors

![interaction modes](/assets/images/2021-11-30-team-topologies-book-notes/interaction_modes.png)

#### X-as-a-Service

- consuming or providing something with minimal collaboration
- clear responsibilities, predictable delivery ("just works")
- focus on Developer Experience

#### Collaboration

- teams working closely together
- drives innovation, use when discovery is needed
- high communication costs
- architecture will be blended due to Conway's Law
- should be used as a temporary mode, establish interfaces and move to X-as-a-Service when possible

#### Facilitating

- helping another team to clear impediments
- reduce gaps in capabilities

Teams always should ask: "What kind of interactions should we have with another team?"

## Team Topologies Core Ideas

![core ideas](/assets/images/2021-11-30-team-topologies-book-notes/core_ideas.png)

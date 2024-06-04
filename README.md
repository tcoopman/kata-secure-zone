# Secure Zone Kata

## Requirements

You have to implement a secure zone.

These are the rules of the secure zone:

1. You can never be alone in a secure zone, either there are 0, 2 or more people in a secure zone.
2. Entering a secure zone needs to be intentional, this means that 2 people trying to access a secure zone via different portals is not allowed.
3. It is allowed to leave via different portals, but you can never be alone, so the last 2 people have to leave together.
4. Once there are 2 people inside, more people can join freely, they don't have to come in via the same portal, nor per 2.

You can use these primitives:

* a badge reader -> reads a badge and gives you badge information
* a secure portal (see assumptions) -> gives access to the exact number of people in that you allowed in

### Assumptions

We recommend you to start with easy mode, and then remove some of the assumptions.

*Easy mode*:

You can make the assumption that you have availability to a secure portal that
only opens when you send an open portal command to it. 

The portal will always let exactly the people in that scanned the badges.
The portal opening will never fail.
The people will always go inside or outside when the portal opens.

*A bit harder*:

You still have a secure portal, but now the portal might fail to open or to
let the people in. When people enter, it's still exactly the exact number of
people that scanned their badges (and you approved)

*Hard mode:*

Design a the secure portal yourself, you have these primitives:

* A gate that you can lock and unlock
* Only 1 person can pass through the gate at a time.
* If you unlock the gate and a person has passed through, the gate is locked again

## Option 1: Modelling

Turn this into a modelling kata.

Design examples and counter examples, do some event storming,...

It's basically up to you how you want to model it, but be rigorous. Make sure
you really understand the implications.

If you want to design an aggregate, use the aggregate modelling tool

![Aggregate Modelling Tool](/pictures/aggregate_modelling_tool.png)

## Option 2: Implementation

Implement a working solution:

You should react when a `badge was read`, you can send `lock` or `unlock` to a
portal, and you should report how many people are inside of the secure zone.

## Extra requirements

1. When there is an emergency, no one should be allowed in and everyone should be allowed to leave.
1. A badge is linked to a role, not all roles are allowed inside.

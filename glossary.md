# Maximo and MAS in Plain English

A glossary for managers, planners, finance and anyone else who hears these terms in meetings and wants the short version. No technical background needed.

New entries are added as the "Maximo Terms, Explained" LinkedIn series goes on.

> **Coming from Maximo 7.6?** The terms below link what you already know to MAS. The recipes in this repository are written and tested for Maximo Manage on MAS only. Don't assume they work as-is on Maximo 7.6.1.x.

## The big three

**IBM Maximo**
The product family name. Most people still use it to mean Maximo Asset Management 7.6, the older system that runs work orders, assets, inventory and purchasing.

**IBM Maximo Application Suite (MAS)**
The newer platform that replaces Maximo 7.6. It's a suite of applications, and you install only the ones you need. Moving to MAS is more than a version upgrade: it means a new platform, a new way of licensing and new skills for the team.

**Maximo Manage (or just "Manage")**
The application inside MAS that does what Maximo 7.6 did. When someone says "we're upgrading Maximo to MAS", they usually mean moving to Manage.

## The rest of the suite

| Application | In one line |
|---|---|
| Monitor | Live readings from sensors on your equipment |
| Health | A score for each asset's condition and risk |
| Predict | Uses past data to forecast when equipment is likely to fail |
| Visual Inspection | Uses AI to spot defects in photos and video |

## Everyday terms

**EAM (Enterprise Asset Management)**
Managing physical things (e.g. pumps, vehicles, buildings) over their whole life: buying, maintaining, repairing and retiring them. Maximo is an EAM system.

**Asset**
Any piece of equipment you track and maintain.

**Work order**
The record of a job: what needs doing, on which asset, by whom, and what it cost.

**AppPoints**
How MAS is licensed. Instead of buying each application separately, you buy a pool of points and spend them on users and applications.

**OpenShift**
The Red Hat platform MAS runs on. It's like the building MAS lives in. Your IT team looks after it, and most users never see it.

**API**
A way for two systems to talk to each other without a person typing in between, e.g. a finance system sending cost codes to Maximo. The [recipes](README.md) in this repository show how it's done.

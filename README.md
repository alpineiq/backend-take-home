# Alpine IQ Take Home

## Overview

This exercise demonstrates how you solve problems using idiomatic go.

## Rules

- **Keep It Confidential**: Please keep this document, the problem,
and your solution confidential even after leaving the interview.
- **48-hour Time Limit**: This should be a relatively short but fun exercise to show
off your knowledge about go and general software engineering principles.
Unless otherwise arranged, complete handoff to Alpine IQ within 48 hours.
- **Use Generally Available Tools**: The team evaluates new releases of tools and
technologies as they become available, however for this exercise, please only use
the latest version of tools and technologies that are considered Generally Available.
- **Open Documentation, Open Internet**: Engineers spend a non-trivial amount of
time sourcing information online; feel free to use online resources and be able to
demonstrate why you selected one approach to solving a problem over another
- **Deliver a Complete Project**: We want to be able to run your solution on our
machines using the test cases you write.
- **Intentionally Ambiguous**: We want to see your approach to the problem and what
decisions you make.

### Technical Objectives

- Implement your solution using a current, released version of Go
- Do not use 3rd party libraries. Use only the core, standard library
- Must include unit tests to verify your components and include these
tests in your solution
- Do not include a graphical user interface of any kind. The quality of code
is evaluated only
- We are looking for a clean, well-factored, idiomatic codebase that has
accompanying unit tests
- Include judicious comments that would be helpful to a fellow team member
that has to review or work in your code.

## Problem

At Alpine IQ we look at contacts ingested from many different sources for a client.
We try to find key points of similarity in those contacts to see if we can find
any that are being duplicated across different sources; then we merge those
records together. For example, a client may have two different CRM systems and
want to see if any contacts exist in both systems and can be merged together.

You need to write a library that will perform this merging process.

### Requirements

1. Once the merge is completed, we should have visbility into what contacts
were merged.
1. Contacts within a single platform should be merged before looking at
contacts from other platforms.

### Examples

#### 1

|          | A          | B                   | C          |
|----------|------------|---------------------|------------|
| phone    | 2135550100 | 4155550199          | 2135550100 |
| email    |            | <test@alpineiq.com> |            |
| state id |            |                     |            |
| platform | CRM 1      | POS1                | CRM 1      |

#### 2

|          | A                   | B                   | C                   |
|----------|---------------------|---------------------|---------------------|
| phone    | 2135550100          | 4155550199          | 2135550100          |
| email    | <test@alpineiq.com> | <test@alpineiq.com> | <test@alpineiq.com> |
| state id | A0001               | A0001               | A0001               |
| platform | CRM 1               | CRM 2               | CRM 3               |

#### 3

|          | A     | B          | C          |
|----------|-------|------------|------------|
| phone    |       | 4155550199 | 2135550100 |
| email    |       |            |            |
| state id | A0001 |            |            |
| platform | CRM 1 | CRM 2      | CRM 3      |

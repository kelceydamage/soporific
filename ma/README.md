# Maintenance SOP

This document describes how we plan, communicate, and execute, and if needed roll back
maintenance of IT assets at Zipline.

## Scope
IT assets.

## Purpose
This procedure is designed to provide an orderly method of performing maintenance operations.

## Policy

### Overview
* Changes to production happen only during maintenance windows.
* Maintenance windows may happen on Thursday evenings after local core hours.
* Maintenance on core infrastructure (not nests) may happen on the first and third weeks of the month.
* Maintenance on nest local (and dependent) infrastructure may happen on the second and fourth weeks.

### Communications
A maintenance window is assumed to happen every Thursday. If it is not needed, the infrastructure team should announce this in #zipline-announcements.

A maintenance plan must be shared with relevant coworkers before it is executed.

### Maintenance Plan 

A maintenance plan is a document that exists as a markdown formatted file in github.
Dates should be in ISO format. Times referenced are UTC only.

It consists of:

* A description of the work involved.
* A method to test this work in a non-production environment.
* A method to validate the work and ensure there were no regressions to operations.
* A method to roll back the work in event of failure.
* A list of stakeholders.

### Execution
The plan should be shared with stakeholders by (at the latest) EOD Monday before the window.


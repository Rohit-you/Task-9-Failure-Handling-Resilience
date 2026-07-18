# Task 9 - Failure Handling & Resilience

Phase 2, Week 3

## What this is

This checks two things: first, whether adding a paywall to applications has quietly hurt match quality, and second, what actually happens when a payment fails - does the student lose money, does an application get created without payment, or does everything roll back cleanly.

## Why this matters

It's easy for a pricing change to accidentally push lower-quality matches to the top, or for a payment failure to leave things in a broken half-done state - student charged but no application, or application created but no payment. This notebook checks both, using real numbers instead of assuming everything's fine.

## What's inside

- Sample student and job data, same as earlier tasks
- Match scores calculated for every student against every job
- The current average match score compared against the pre-payment baseline to check for any quality drop
- A simple tolerance check - a small natural fluctuation is fine, anything past that gets flagged as a regression
- A payment simulation where some transactions succeed and some fail on purpose, to confirm failed payments never create an application and never take money

## What it found

Average match score stayed at 0.413 before and after payment was introduced, so no regression was detected. In the payment test, every failed transaction correctly left no money taken and no application created - nothing gets stuck in a half-finished state.

## How to run it

Open the notebook and run every cell in order. No external files needed, the data is generated inside the notebook.

## Requirements

- pandas
- numpy

## Where it stands

The conversion-quality check is built and demoed live, comparing real before/after numbers rather than assuming quality held up. Payment failure handling is included and shown to fail safely, not silently.

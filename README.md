# PulsePay

**Instant payments that never leave you unsure.**

PulsePay picks the fastest, most reliable route for each payment and lets you track it every step of the way.
Built for the DRUNIX Hackathon (NPCI x Citi), Real-Time Payments track, by Team Phishermen.

> **Status:** idea and design stage. The prototype will be built in the coding phase.

## The problem

UPI handles about 24 billion payments a month (NPCI data, September 2026), and most of them work. But at that size, even a small share of delays and failures affects millions of people. The worst case is a payment that times out and leaves the sender unsure whether the money moved. Tapping pay again risks paying twice, and retrying the same slow route wastes time.

## What PulsePay is

A smart add-on that sits between payment apps or banks and payment systems like UPI and IMPS. It does not replace UPI and does not hold or move money itself.

**Payment app or bank → PulsePay → UPI / IMPS**, with a small advisor that predicts which payments may be slow or fail, and a shared record of every payment on DRUNIX.

## How DRUNIX is used

PulsePay uses DRUNIX, NPCI's open-source blockchain platform, as the shared record of every payment.

- **Chaincode (Java):** creates a payment record, refuses a second record with the same unique ID, adds each step, and returns the status.
- **Multi-organisation network:** the sender's bank, the receiving bank and the payment app are all members, so they see the same record and no one can change it alone.
- **State database that can search by field** (such as CouchDB or YugabyteDB): lets the bank screen list payments by status, for example all unclear payments.

## Three promises

1. **No double payments.** Every payment has a unique ID, so sending the same request again never charges twice.
2. **No money in limbo.** Every payment is always accounted for. If a payment fails after the money is taken, the bank returns it and PulsePay follows the refund until it arrives. If a result is unclear, PulsePay checks what really happened first, and only tries another option once the first one confirms it failed.
3. **A record nobody can quietly change.** Every step of a payment is saved on a shared DRUNIX network that the banks and the app all take part in.

The advisor only gives advice. The safety rules do not depend on it.

## Plan

1. Set up the project and bring up a small DRUNIX test network
2. Accounts, payment records, no double payments
3. Simulated payment systems that slow down or fail, refund tracking
4. Connect the chaincode, add the advisor, smart choice of payment system, live status and bank screens
5. Testing, packaging, demo

## Honest note

The prototype will use simulated banks and payment systems with practice data we create ourselves, so we make no claim about real-world accuracy. It is designed to connect to real payment APIs, such as NPCI's, later.

## Tech stack

Java, Spring Boot, Spring Data JPA, Thymeleaf, H2 | Python, FastAPI, pandas, scikit-learn, XGBoost | DRUNIX (chaincode in Java) | Docker

## Team Phishermen

Sarvesh Senthilkumar, Anuraag Ravi, Pragathi Sivaji, Thaneesh Prakash

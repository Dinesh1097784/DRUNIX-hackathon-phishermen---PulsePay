# DRUNIX-hackathon-phishermen---PulsePay
Reliable real-time transfers with no double payments and smart failure recovery. DRUNIX Hackathon, Real-Time Payments

# PulsePay

Reliable instant transfers with smart failure recovery.
DRUNIX Hackathon (with Citi), Real-Time Payments track.
*Status: proposal stage, prototype in progress.*

**Problem:** Instant payments only feel instant when they work. When a transfer is slow or fails, senders can't tell if the money moved, and retrying can charge them twice.

**Solution**
- **No double payments:** every request has a unique key.
- **No lost money:** double-entry ledger with automatic reversal on failure.
- **Verifiable history:** hash-chained, tamper-evident ledger.
- **Smart recovery:** a Python advisor predicts slow or failing transfers and suggests when to retry or which route to use.

**Architecture:** `java-service/` (Spring Boot payment switch) + `python-service/` (FastAPI advisor), talking over JSON REST and run together with Docker Compose. Uses simulated banks and synthetic data.

**Stack:** Java, Spring Boot, Spring Data JPA, Thymeleaf, Python, FastAPI, scikit-learn, XGBoost, Docker

**Team:** Sarvesh Senthilkumar, Anuraag Ravi, Pragathi Sivaji, Thaneesh Prakash

> **FICTIONAL DEMO DATA.** Moishe Zuchmir, KugelCloud and everything in this file are invented to demonstrate one-memory. Any resemblance to real people or companies is coincidental.

# KugelCloud Booking Engine

- **Kind:** work
- **Status:** active
- **My role:** tech lead for the Booking & Orders domain (a team of four)
- **Stack:** Java 21, Spring Boot 3, Spring Modulith, PostgreSQL 16, Kafka, Flyway, Testcontainers, Kubernetes on AWS
- **Started:** 2021-06

## What it is

The core of KugelCloud: hall availability, tentative holds, contracts and deposits, guest counts, and menu orders that turn into kitchen production sheets ("how many kilos of potato kugel for 340 guests?"). About 120 caterers and event halls use it, and load triples in wedding season (June, and September to October).

## Current state

- Booking and Orders are being extracted from "Cholent", the original 2019 monolith (everything went into one pot, and it has been simmering ever since), as Spring Modulith modules ([0001](../decisions/0001-modular-monolith.md)). Booking is done; Orders is about 60% done.
- Events reach Kafka through a transactional outbox, in production since 2025-07 ([0002](../decisions/0002-transactional-outbox.md)).
- No double bookings since tentative holds moved to a PostgreSQL exclusion constraint on hall and time range.
- The bookings table is partitioned by event month.

## Key decisions

- [0001: Modular monolith instead of microservices](../decisions/0001-modular-monolith.md)
- [0002: Transactional outbox for Kafka events](../decisions/0002-transactional-outbox.md)
- [0006: Saga style for multi-vendor orders](../decisions/0006-multi-vendor-order-saga.md) (proposed)

## Open questions

- How to coordinate orders that involve several vendors when one of them declines: see 0006.
- Whether Kitchen Planning should be the next module to extract, or the first to scale on its own during wedding season.
- How to model late guest-count changes, the most common cause of compensating transactions in this domain.

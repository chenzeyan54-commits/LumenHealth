# LumenHealth.

**LumenHealth** is a clinical operations platform designed to help healthcare facilities manage patients, staff workflows, encounters, and billing in a unified system.

The platform combines web, mobile, and backend services with a dedicated Stellar integration layer for financial and billing workflows, enabling a modern healthcare system that is structured, auditable, and scalable.

LumenHealth is built as a monorepo to support fast iteration across clinical, administrative, and operational features.

---

## Overview

Healthcare systems often operate across fragmented tools — patient records in one system, scheduling in another, billing handled separately, and mobile workflows poorly integrated.

LumenHealth addresses this by providing a unified platform for:

* clinic and staff management,
* patient records and histories,
* clinical encounters and workflows,
* billing and payment processing,
* mobile-first access for healthcare workers,
* structured, auditable data across all operations.

The system is designed to support both administrative and frontline clinical use cases.

---

## Core Modules

## Authentication & Access Control

LumenHealth begins with a secure authentication and role system.

It supports:

* staff login and identity verification,
* role-based access (admin, clinician, support staff),
* secure session management,
* scoped permissions per clinic or organization.

This forms the foundation for all clinical and administrative actions.

---

## Clinic & Staff Management

The platform supports structured clinic organization management.

Capabilities include:

* clinic onboarding,
* staff assignment and roles,
* multi-clinic support,
* access scoping per facility,
* administrative oversight tools.

This ensures healthcare environments can be modeled accurately within the system.

---

## Patient Records

Patient data is central to LumenHealth.

The system provides:

* patient profiles,
* medical history tracking,
* visit records,
* structured clinical data storage,
* longitudinal patient context,
* secure access controls.

All patient data is designed to be consistent, traceable, and easy to extend.

---

## Encounters & Clinical Workflows

Encounters represent interactions between clinicians and patients.

The system supports:

* visit creation and updates,
* diagnosis and notes,
* treatment workflows,
* structured encounter timelines,
* follow-up tracking,
* clinician collaboration.

This creates a clear record of clinical activity over time.

---

## Billing & Stellar Integration

LumenHealth uses Stellar to support financial workflows within healthcare operations.

The Stellar service enables:

* billing event processing,
* payment tracking,
* transaction receipts,
* audit-friendly financial records,
* integration between clinical actions and billing events.

This provides a transparent and programmable layer for healthcare billing workflows.

---

## Mobile & Offline Support

The mobile workspace is designed for frontline healthcare environments.

It supports:

* patient lookup and access,
* encounter documentation,
* offline-first workflows (future phase),
* sync when connectivity is restored,
* lightweight clinical data entry.

This ensures clinicians can operate even in low-connectivity environments.

---

## System Architecture

LumenHealth is built as a strict monorepo with clear boundaries between services.

| Layer              | Technology             |
| ------------------ | ---------------------- |
| API                | NestJS + TypeScript    |
| Web                | Next.js App Router     |
| Mobile             | React Native workspace |
| Blockchain/Billing | Stellar service        |
| Shared Config      | @lumen/config          |
| Shared Types       | @lumen/types           |

### API Architecture

The API layer follows NestJS conventions:

- **Modules** — feature-scoped modules (`AuthModule`, `ClinicModule`, `PatientModule`, `EncounterModule`, `BillingModule`, `StellarModule`) encapsulate related controllers, providers, and services.
- **Guards** — `JwtAuthGuard` and `RolesGuard` enforce authentication and role-based access at the route level.
- **Pipes** — `ValidationPipe` with class-validator DTOs handles request validation and transformation.
- **Filters** — `HttpExceptionFilter` and `AllExceptionsFilter` centralize error handling and normalize API error responses.
- **Dependency Injection** — NestJS's IoC container wires providers across modules via constructor injection.

---

## Repository Structure
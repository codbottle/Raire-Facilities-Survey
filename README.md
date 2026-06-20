# RFS — Raire Facilities Survey

RFS is a mobile-first property assessment and asset management platform designed to transform facility inspections into actionable intelligence.

Built initially for hotel operations, RFS helps inspectors, maintenance personnel, property owners, and facility managers perform detailed room-by-room, area-by-area, and system-by-system evaluations while documenting conditions, assets, deficiencies, repair priorities, and estimated costs.

## Initial Target

The first deployment target is the Quality Inn hotel modernization survey workflow:

- Room-by-room inspections
- Bathroom fixture inventories
- PTAC and HVAC assessments
- Plumbing condition surveys
- Water intrusion and damage tracking
- Exterior and roof inspections
- Common area evaluations
- Asset inventory management
- Photo documentation
- Deficiency code tracking
- Repair cost estimation
- Capital improvement planning
- Property condition scoring
- Grant and incentive qualification reporting

## Core Data Flow

Property → Building → Area / Room → Inspection → Asset → Deficiency → Photo → Report

## Version 1 Goal

Create a simple mobile-first inspection system that allows a user to:

1. Select a property.
2. Select a room or area.
3. Complete an inspection checklist.
4. Record asset information.
5. Add deficiencies and severity.
6. Attach photos.
7. Generate repair and capital planning reports.

## Technology Direction

- Frontend: Mobile-first web app / PWA
- Backend: Cloudflare Workers
- Database: Cloudflare D1
- File Storage: Cloudflare R2
- Future: Android wrapper if needed

## Mission

Turn facilities from collections of unknown problems into measurable, trackable, and manageable assets.

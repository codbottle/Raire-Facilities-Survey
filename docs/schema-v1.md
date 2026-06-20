# RFS Schema V1

This document defines the first working data model for Raire Facilities Survey.

The goal of V1 is simple: collect useful facility inspection data from a mobile device and turn it into repair lists, asset inventories, capital plans, and grant-supporting documentation.

## Core Flow

Property -> Building -> Area / Room -> Inspection -> Asset -> Deficiency -> Photo -> Report

## Core Tables

### properties

Represents a facility or site.

Fields:
- id
- name
- address
- owner_name
- management_company
- franchise_brand
- notes
- created_at
- updated_at

### buildings

Represents buildings or major structures on a property.

Fields:
- id
- property_id
- name
- building_type
- year_built
- square_feet
- notes
- created_at
- updated_at

### areas

Represents non-room spaces such as lobby, hallway, laundry, roof, restaurant, parking lot, mechanical room, or exterior zones.

Fields:
- id
- property_id
- building_id
- area_type
- name
- floor
- notes
- created_at
- updated_at

### rooms

Represents individual rentable rooms or units.

Fields:
- id
- property_id
- building_id
- room_number
- floor
- wing
- room_type
- status
- occupied
- out_of_service
- notes
- created_at
- updated_at

### inspections

Represents one inspection event for a room or area.

Fields:
- id
- property_id
- building_id
- room_id
- area_id
- inspection_type
- inspector_name
- inspection_date
- overall_score
- priority
- room_ready
- immediate_repair_required
- estimated_total_cost
- notes
- created_at
- updated_at

### inspection_items

Stores checklist answers from inspection forms.

Fields:
- id
- inspection_id
- category
- item_name
- condition
- value
- severity
- needs_repair
- estimated_cost
- notes
- created_at
- updated_at

### assets

Tracks equipment, fixtures, and physical components.

Examples:
- PTAC
- toilet
- sink faucet
- shower valve
- mirror
- water heater
- pump
- exterior light

Fields:
- id
- property_id
- building_id
- room_id
- area_id
- asset_type
- manufacturer
- model
- serial_number
- cartridge_number
- faucet_type
- install_date
- condition
- notes
- created_at
- updated_at

### deficiencies

Tracks problems found during inspections.

Fields:
- id
- inspection_id
- property_id
- building_id
- room_id
- area_id
- asset_id
- code
- category
- description
- severity
- status
- estimated_cost
- assigned_to
- due_date
- notes
- created_at
- updated_at

### photos

Stores photo references for inspections, assets, and deficiencies.

Fields:
- id
- property_id
- inspection_id
- room_id
- area_id
- asset_id
- deficiency_id
- storage_key
- caption
- created_at

### reports

Stores generated report metadata.

Fields:
- id
- property_id
- report_type
- title
- generated_by
- generated_at
- storage_key
- notes

## Inspection Types

- room
- bathroom
- common_area
- exterior
- roof
- mechanical
- restaurant
- laundry
- parking_lot

## Priority Levels

- critical
- high
- medium
- low
- monitor

## Severity Levels

- critical
- high
- medium
- low

## Room Status Options

- rentable
- occupied
- vacant
- out_of_service
- needs_repair
- under_renovation

## V1 Rule

Do not overbuild.

The first app only needs to capture:

1. Where the inspection happened.
2. What was inspected.
3. What condition it was in.
4. What needs repair.
5. What it may cost.
6. What photos prove it.

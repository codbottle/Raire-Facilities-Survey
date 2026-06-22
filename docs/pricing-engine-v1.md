# RFS Pricing Engine V1

The RFS Pricing Engine links inspected assets, part numbers, vendor sources, labor assumptions, and repair quantities into live or semi-live cost estimates.

The goal is to turn inspection findings into owner-ready, investor-ready, and grant-ready cost projections.

## Core Concept

Inspection data tells us what is wrong.

Asset data tells us what part is needed.

Pricing data tells us what it will cost.

Reports tell the owner what to do next.

```text
Asset → Part Number → Vendor Source → Price → Quantity → Labor → Total Estimate → Capital Plan
```

## V1 Rule

Do not depend on scraping or unofficial vendor access.

V1 supports:

- Manual price entry
- Saved vendor links
- Last-known price
- Price checked date
- Preferred vendor
- Alternate vendors
- Labor hours
- Labor rate
- Quantity required
- Cost rollups by room, system, deficiency, and property

Live vendor lookup can be added later only through approved APIs, affiliate feeds, procurement integrations, or legally permitted catalog access.

## Pricing Engine Fields

### parts

Represents a replacement part, fixture, material, or component.

Fields:

- id
- part_number
- manufacturer
- name
- description
- category
- unit_type
- notes
- created_at
- updated_at

Examples:

- Delta RP46074 shower cartridge
- Moen 1222 cartridge
- PTAC filter
- Sink drain gasket
- Toilet fill valve
- Wax ring
- PTAC sleeve seal kit
- GFCI outlet

### vendors

Represents a supplier or pricing source.

Fields:

- id
- name
- website_url
- vendor_type
- notes
- created_at
- updated_at

Examples:

- Home Depot
- Lowe's
- Ferguson
- SupplyHouse
- Grainger
- Amazon Business
- Local plumbing supplier
- Local HVAC supplier

### vendor_prices

Stores known pricing for a part from a vendor.

Fields:

- id
- part_id
- vendor_id
- vendor_sku
- vendor_url
- price
- currency
- unit_type
- availability_status
- price_checked_at
- source_type
- notes
- created_at
- updated_at

source_type options:

- manual
- receipt
- quote
- api
- catalog
- import

availability_status options:

- in_stock
- limited
- out_of_stock
- unknown

### asset_parts

Links assets to common replacement parts.

Fields:

- id
- asset_id
- part_id
- relationship_type
- notes
- created_at
- updated_at

relationship_type examples:

- cartridge
- filter
- gasket
- seal
- valve
- motor
- control_board
- replacement_unit

### repair_estimates

Represents a repair estimate generated from an inspection or deficiency.

Fields:

- id
- property_id
- building_id
- room_id
- area_id
- inspection_id
- deficiency_id
- asset_id
- title
- status
- priority_color
- labor_hours
- labor_rate
- parts_total
- labor_total
- other_total
- estimate_total
- notes
- created_at
- updated_at

priority_color options:

- green
- yellow
- orange
- red

### repair_estimate_parts

Line items for repair estimates.

Fields:

- id
- repair_estimate_id
- part_id
- vendor_price_id
- quantity
- unit_price
- line_total
- notes
- created_at
- updated_at

## Color Priority Model

RFS should use color-first decision language.

| Color | Meaning | Owner Action |
|---|---|---|
| Green | Healthy | No action required |
| Yellow | Functional but aging | Monitor / budget |
| Orange | Needs repair | Plan action |
| Red | Failed / critical | Immediate action |

## Cost Rollups

The pricing engine must support rollups by:

- property
- building
- room
- area
- asset type
- deficiency code
- priority color
- vendor
- inspection date range

Example owner dashboard:

```text
Red Repairs: $18,400
Orange Repairs: $42,700
Yellow Budget Items: $31,200
Green Assets: $0
```

## Example Flow

Room 214 inspection finds:

- Sink drain gasket failed
- Faucet manufacturer: Delta
- Drain assembly condition: failed

RFS suggests:

- Deficiency code: PLMB-002
- Part category: sink drain gasket / drain assembly
- Priority color: Orange

Inspector selects saved part:

- Delta lavatory drain assembly
- Preferred vendor: Home Depot
- Last known price: $18.97
- Quantity: 1
- Labor: 0.5 hours
- Labor rate: $85/hr

Estimate:

```text
Parts: $18.97
Labor: $42.50
Total: $61.47
```

After 22 rooms:

```text
Failed drain gaskets: 22
Parts total: $417.34
Labor total: $935.00
Repair total: $1,352.34
```

## Vendor Strategy

### V1

Manual price records and vendor links.

### V2

CSV import from supplier quotes, receipts, or exported carts.

### V3

Approved APIs, affiliate catalog feeds, procurement integrations, or vendor partnerships.

### V4

Automatic refresh of known prices and availability.

## Why This Matters

Inspection without pricing creates a punch list.

Inspection with pricing creates a capital plan.

Capital plans create owner decisions.

Owner decisions create revenue.

# RFS Deficiency Code Library V1

Deficiency codes allow inspections to become structured data instead of loose notes.

Each code should identify:

- Category
- Problem type
- Severity
- Typical repair action
- Estimated cost range

## PTAC / HVAC

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| PTAC-001 | Dirty PTAC filter | Low | Clean or replace filter |
| PTAC-002 | PTAC coils need cleaning | Medium | Clean evaporator/condenser coils |
| PTAC-003 | PTAC cooling failed | High | Diagnose compressor, controls, refrigerant circuit |
| PTAC-004 | PTAC heating failed | High | Diagnose heat strip, controls, board |
| PTAC-005 | PTAC fan failed | High | Diagnose fan motor/capacitor/control |
| PTAC-006 | PTAC excessive noise | Medium | Inspect fan wheel, bearings, mount |
| PTAC-007 | PTAC condensate drain restricted | High | Clear drain and inspect pan |
| PTAC-008 | PTAC sleeve penetration leaking | High | Seal interior/exterior penetration |
| PTAC-009 | PTAC wall damage present | Medium | Repair wall after source is corrected |
| PTAC-010 | PTAC floor damage present | Medium | Repair floor after source is corrected |

## Plumbing

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| PLMB-001 | Leaking sink faucet | Medium | Repair cartridge or replace faucet |
| PLMB-002 | Failed sink drain gasket | Medium | Replace drain gasket/assembly |
| PLMB-003 | Leaking supply stop | High | Replace stop valve |
| PLMB-004 | Leaking supply line | High | Replace supply line |
| PLMB-005 | Toilet fill valve needs service | Medium | Replace fill valve |
| PLMB-006 | Toilet flapper needs service | Low | Replace flapper |
| PLMB-007 | Toilet loose at floor | High | Reset toilet and inspect flange |
| PLMB-008 | Toilet wax ring suspected failed | High | Reset toilet and inspect subfloor |
| PLMB-009 | Shower valve cartridge failed | Medium | Identify cartridge and replace |
| PLMB-010 | Low water pressure | Medium | Diagnose aerator, valve, supply issue |

## Bathroom Finish

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| BATH-001 | Failed tub/shower caulk | Medium | Remove and recaulk |
| BATH-002 | Failed toilet base caulk | Low | Recaulk after confirming no leak |
| BATH-003 | Loose tile | Medium | Repair tile and substrate as needed |
| BATH-004 | Missing tile | Medium | Replace tile |
| BATH-005 | Failed grout | Medium | Regrout or seal |
| BATH-006 | Bathroom water intrusion visible | High | Identify source before cosmetic repair |
| BATH-007 | Vanity water damage | Medium | Repair/replace vanity |
| BATH-008 | Exhaust fan failed | Medium | Repair/replace fan |
| BATH-009 | Exhaust fan excessive noise | Low | Clean or replace fan |

## Walls / Paint / Ceiling

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| WALL-001 | Spot paint required | Low | Touch-up paint |
| WALL-002 | Full room paint required | Medium | Repaint room |
| WALL-003 | Drywall damage | Medium | Patch and paint |
| WALL-004 | Water stain on wall | High | Confirm source before repair |
| CEIL-001 | Ceiling stain | High | Confirm source before repair |
| CEIL-002 | Ceiling sagging | Critical | Inspect immediately |
| CEIL-003 | Ceiling repair needed | Medium | Patch and paint |

## Flooring

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| FLR-001 | Flooring replacement needed | Medium | Estimate by room/area |
| FLR-002 | Soft floor area | High | Inspect subfloor |
| FLR-003 | Water damaged floor | High | Confirm source before repair |
| FLR-004 | Trip hazard | High | Repair immediately |
| FLR-005 | Damaged tile | Medium | Replace tile |

## Doors / Windows / Exterior Openings

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| DOOR-001 | Entry door damaged | Medium | Repair/replace door |
| DOOR-002 | Weatherstripping failed | Medium | Replace weatherstripping |
| DOOR-003 | Lockset issue | High | Repair/replace lock |
| WIN-001 | Window screen damaged | Low | Repair/replace screen |
| WIN-002 | Window screen missing | Low | Replace screen |
| WIN-003 | Window lock failed | Medium | Repair/replace lock |
| WIN-004 | Window caulking failed | Medium | Recaulk |
| WIN-005 | Window water intrusion | High | Identify source and repair |

## Safety / Electrical

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| ELEC-001 | Light fixture failed | Low | Repair/replace fixture |
| ELEC-002 | Outlet damaged | High | Replace outlet |
| ELEC-003 | GFCI failed | High | Replace GFCI |
| SAFE-001 | Trip hazard | High | Repair immediately |
| SAFE-002 | Emergency light failed | High | Repair/replace |
| SAFE-003 | Exit sign failed | High | Repair/replace |
| SAFE-004 | Fire extinguisher missing/expired | High | Correct immediately |

## Exterior / Roof / Drainage

| Code | Description | Default Severity | Notes |
|---|---|---|---|
| EXT-001 | Exterior caulking failed | Medium | Recaulk |
| EXT-002 | Exterior wall damage | Medium | Repair exterior finish |
| EXT-003 | Parking lot pothole | Medium | Patch/repair |
| EXT-004 | Exterior lighting failed | High | Repair/replace |
| EXT-005 | Standing water/drainage issue | High | Correct drainage |
| ROOF-001 | Suspected roof leak | High | Inspect roof area |
| ROOF-002 | Confirmed roof leak | Critical | Repair immediately |
| ROOF-003 | Roof penetration not sealed | High | Seal penetration |
| ROOF-004 | Roof drain blocked | High | Clear drain |

## Status Options

- open
- assigned
- in_progress
- resolved
- deferred
- monitor

## Severity Rule

Critical = active life safety issue, active water intrusion, structural concern, or major system failure.

High = likely to cause damage, lost revenue, guest complaint, or operational risk.

Medium = should be planned and budgeted.

Low = cosmetic or routine maintenance.

# Common Area Inspection Form V1

This form is for inspecting shared interior areas such as lobby, hallways, laundry, office, stairwells, restaurant, vending areas, and mechanical support spaces.

## Purpose

Common areas directly affect guest perception, safety, insurance risk, brand compliance, and capital planning.

## Inspection Header

| Field | Type | Required | Notes |
|---|---|---:|---|
| property_id | relation | yes | Selected property |
| building_id | relation | no | Selected building |
| area_id | relation | yes | Selected area |
| area_type | select | yes | lobby/hallway/laundry/restaurant/office/stairwell/mechanical/vending/other |
| inspector_name | text | yes | Person performing inspection |
| inspection_date | datetime | yes | Defaults to current time |
| priority | select | yes | critical/high/medium/low/monitor |
| immediate_repair_required | boolean | yes | Requires urgent attention |
| estimated_total_cost | money | no | Calculated or entered |
| notes | long_text | no | General notes |

## Area Condition

| Field | Type | Options |
|---|---|---|
| cleanliness_condition | score | 0-4 |
| paint_condition | score | 0-4 |
| flooring_condition | score | 0-4 |
| ceiling_condition | score | 0-4 |
| wall_condition | score | 0-4 |
| odor_issue | boolean | yes/no |
| guest_facing_issue | boolean | yes/no |
| area_condition_notes | long_text | optional |

## Water Damage / Moisture

| Field | Type | Options |
|---|---|---|
| water_damage_present | boolean | yes/no |
| ceiling_stains | boolean | yes/no |
| wall_stains | boolean | yes/no |
| floor_water_damage | boolean | yes/no |
| active_leak_suspected | boolean | yes/no |
| mold_concern | boolean | yes/no |
| source_identified | boolean | yes/no |
| suspected_source | text | optional |
| water_damage_notes | long_text | optional |

## Electrical / Lighting

| Field | Type | Options |
|---|---|---|
| lighting_working | boolean | yes/no |
| emergency_lighting_working | boolean | yes/no/unknown |
| exit_sign_working | boolean | yes/no/unknown |
| outlets_condition | score | 0-4 |
| exposed_wiring | boolean | yes/no |
| electrical_panel_present | boolean | yes/no |
| electrical_notes | long_text | optional |

## HVAC / Comfort

| Field | Type | Options |
|---|---|---|
| temperature_acceptable | boolean | yes/no |
| humidity_concern | boolean | yes/no |
| hvac_noise | select | normal/excessive/none |
| ventilation_adequate | boolean | yes/no/unknown |
| hvac_notes | long_text | optional |

## Life Safety / Liability

| Field | Type | Options |
|---|---|---|
| trip_hazard_present | boolean | yes/no |
| slip_hazard_present | boolean | yes/no |
| handrail_condition | score | 0-4/not_applicable |
| fire_extinguisher_present | boolean | yes/no/unknown |
| fire_extinguisher_current | boolean | yes/no/unknown |
| blocked_exit | boolean | yes/no |
| safety_notes | long_text | optional |

## Doors / Access

| Field | Type | Options |
|---|---|---|
| door_condition | score | 0-4/not_applicable |
| lock_condition | score | 0-4/not_applicable |
| closer_working | boolean | yes/no/not_applicable |
| access_control_issue | boolean | yes/no |
| door_notes | long_text | optional |

## Furniture / Fixtures / Guest Touchpoints

| Field | Type | Options |
|---|---|---|
| furniture_condition | score | 0-4/not_applicable |
| signage_condition | score | 0-4/not_applicable |
| vending_condition | score | 0-4/not_applicable |
| ice_machine_condition | score | 0-4/not_applicable |
| guest_touchpoint_notes | long_text | optional |

## Photos

Photos may be attached to:

- area inspection
- deficiency
- asset

Required photo categories when issue exists:

- water damage
- safety hazard
- failed lighting
- damaged flooring
- active leak
- visible mold concern

## Suggested Deficiency Triggers

| Trigger | Suggested Code |
|---|---|
| water_damage_present = yes | WALL-004 or CEIL-001 |
| active_leak_suspected = yes | ROOF-001 or PLMB custom code |
| trip_hazard_present = yes | SAFE-001 |
| emergency_lighting_working = no | SAFE-002 |
| exit_sign_working = no | SAFE-003 |
| fire_extinguisher_present = no | SAFE-004 |
| lighting_working = no | ELEC-001 |
| exposed_wiring = yes | ELEC custom critical code |

## V1 Rule

Common area inspections should separate guest-facing appearance issues from life-safety issues.

A stained wall is cosmetic unless the source is active.

An exit sign failure is not cosmetic. It is a compliance issue.

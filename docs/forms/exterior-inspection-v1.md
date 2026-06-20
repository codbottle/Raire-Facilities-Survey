# Exterior Inspection Form V1

This form is for inspecting the outside of a property by zone.

Examples:

- Front entrance
- Rear entrance
- Parking lot east
- Parking lot west
- Building exterior north
- Building exterior south
- Dumpster area
- Restaurant exterior
- Pool area
- Sidewalks
- Drainage zones
- Signage
- Roof access exterior

## Purpose

Exterior conditions affect curb appeal, guest safety, water intrusion risk, insurance exposure, brand compliance, and long-term capital planning.

## Inspection Header

| Field | Type | Required | Notes |
|---|---|---:|---|
| property_id | relation | yes | Selected property |
| building_id | relation | no | Selected building |
| area_id | relation | yes | Selected exterior area/zone |
| exterior_zone_type | select | yes | entrance/parking/building_wall/sidewalk/drainage/roof_access/signage/dumpster/pool/other |
| inspector_name | text | yes | Person performing inspection |
| inspection_date | datetime | yes | Defaults to current time |
| weather_condition | select | no | dry/rain/snow/ice/windy/unknown |
| priority | select | yes | critical/high/medium/low/monitor |
| immediate_repair_required | boolean | yes | Requires urgent attention |
| estimated_total_cost | money | no | Calculated or entered |
| notes | long_text | no | General notes |

## Building Exterior

| Field | Type | Options |
|---|---|---|
| exterior_wall_condition | score | 0-4 |
| siding_condition | score | 0-4/not_applicable |
| masonry_condition | score | 0-4/not_applicable |
| stucco_condition | score | 0-4/not_applicable |
| paint_condition | score | 0-4/not_applicable |
| exterior_caulk_condition | score | 0-4 |
| cracks_present | boolean | yes/no |
| holes_or_openings_present | boolean | yes/no |
| pest_entry_points | boolean | yes/no |
| exterior_notes | long_text | optional |

## Windows / Openings

| Field | Type | Options |
|---|---|---|
| window_exterior_condition | score | 0-4/not_applicable |
| window_caulk_condition | score | 0-4/not_applicable |
| visible_window_leaks | boolean | yes/no |
| door_exterior_condition | score | 0-4/not_applicable |
| weatherstripping_condition | score | 0-4/not_applicable |
| openings_notes | long_text | optional |

## PTAC / Wall Penetrations

| Field | Type | Options |
|---|---|---|
| ptac_sleeves_visible | boolean | yes/no |
| ptac_exterior_seals_condition | score | 0-4/not_applicable |
| ptac_penetrations_open | boolean | yes/no |
| staining_below_ptac | boolean | yes/no |
| wall_damage_around_ptac | boolean | yes/no |
| penetration_notes | long_text | optional |

## Roof Edge / Gutters / Downspouts

| Field | Type | Options |
|---|---|---|
| roof_edge_condition | score | 0-4/not_applicable |
| gutters_present | boolean | yes/no |
| gutter_condition | score | 0-4/not_applicable |
| downspouts_condition | score | 0-4/not_applicable |
| downspouts_discharge_away | boolean | yes/no/unknown |
| fascia_soffit_condition | score | 0-4/not_applicable |
| roof_edge_notes | long_text | optional |

## Parking Lot / Pavement

| Field | Type | Options |
|---|---|---|
| pavement_condition | score | 0-4/not_applicable |
| potholes_present | boolean | yes/no |
| pothole_severity | select | none/minor/moderate/severe |
| striping_condition | score | 0-4/not_applicable |
| ada_spaces_visible | boolean | yes/no/unknown |
| curb_condition | score | 0-4/not_applicable |
| parking_notes | long_text | optional |

## Sidewalks / Walkways / Stairs

| Field | Type | Options |
|---|---|---|
| sidewalk_condition | score | 0-4/not_applicable |
| trip_hazard_present | boolean | yes/no |
| stair_condition | score | 0-4/not_applicable |
| handrail_condition | score | 0-4/not_applicable |
| slip_hazard_present | boolean | yes/no |
| walkway_notes | long_text | optional |

## Drainage / Water Control

| Field | Type | Options |
|---|---|---|
| standing_water_present | boolean | yes/no |
| erosion_present | boolean | yes/no |
| drainage_away_from_building | boolean | yes/no/unknown |
| clogged_drain_present | boolean | yes/no |
| grading_issue_suspected | boolean | yes/no |
| drainage_notes | long_text | optional |

## Exterior Lighting / Security

| Field | Type | Options |
|---|---|---|
| parking_lot_lighting_working | boolean | yes/no/unknown |
| building_lighting_working | boolean | yes/no/unknown |
| entrance_lighting_working | boolean | yes/no/unknown |
| dark_areas_present | boolean | yes/no |
| camera_present | boolean | yes/no/unknown |
| lighting_notes | long_text | optional |

## Signage / Curb Appeal

| Field | Type | Options |
|---|---|---|
| main_sign_condition | score | 0-4/not_applicable |
| directional_signage_condition | score | 0-4/not_applicable |
| landscaping_condition | score | 0-4/not_applicable |
| trash_debris_present | boolean | yes/no |
| dumpster_area_condition | score | 0-4/not_applicable |
| curb_appeal_notes | long_text | optional |

## Pool Area If Present / Shut Down

| Field | Type | Options |
|---|---|---|
| pool_present | boolean | yes/no |
| pool_operational | boolean | yes/no/not_applicable |
| pool_secured | boolean | yes/no/not_applicable |
| pool_deck_condition | score | 0-4/not_applicable |
| pool_fence_condition | score | 0-4/not_applicable |
| pool_liability_concern | boolean | yes/no |
| pool_notes | long_text | optional |

## Photos

Photos may be attached to:

- exterior area inspection
- specific asset
- deficiency
- repair zone

Required photo categories when issue exists:

- trip hazard
- standing water
- wall opening
- exterior water intrusion
- PTAC penetration issue
- pothole
- failed lighting
- pool liability concern

## Suggested Deficiency Triggers

| Trigger | Suggested Code |
|---|---|
| exterior_caulk_condition <= 1 | EXT-001 |
| holes_or_openings_present = yes | EXT-002 |
| potholes_present = yes | EXT-003 |
| parking_lot_lighting_working = no | EXT-004 |
| standing_water_present = yes | EXT-005 |
| trip_hazard_present = yes | SAFE-001 |
| ptac_penetrations_open = yes | PTAC-008 |
| staining_below_ptac = yes | PTAC-008 |
| visible_window_leaks = yes | WIN-005 |
| clogged_drain_present = yes | ROOF-004 |
| pool_secured = no | SAFE custom critical code |

## V1 Rule

Exterior inspections must focus on two things first:

1. Water getting into the building.
2. People getting hurt outside the building.

Curb appeal matters, but water intrusion and liability come first.

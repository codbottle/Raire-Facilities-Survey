# Room Inspection Form V1 — Hybrid

This form is designed for fast mobile inspections with optional deep asset expansion.

Default workflow:

1. Select room.
2. Complete quick condition checks.
3. Expand only the assets that need deeper inspection.
4. Add deficiencies.
5. Add photos.
6. Save inspection.

## Inspection Header

| Field | Type | Required | Notes |
|---|---|---:|---|
| property_id | relation | yes | Selected property |
| building_id | relation | no | Selected building |
| room_id | relation | yes | Selected room |
| inspector_name | text | yes | Person performing inspection |
| inspection_date | datetime | yes | Defaults to current time |
| occupied | boolean | yes | Yes/No |
| out_of_service | boolean | yes | Yes/No |
| room_ready | boolean | yes | Can this room be rented today? |
| immediate_repair_required | boolean | yes | Requires urgent attention |
| priority | select | yes | critical/high/medium/low/monitor |
| overall_score | integer | no | 0-100, calculated later |
| notes | long_text | no | General notes |

## Scoring Scale

Use this scale for condition-based fields:

| Score | Label | Meaning |
|---:|---|---|
| 4 | Excellent | New or near-new condition |
| 3 | Good | Functional, minor wear |
| 2 | Fair | Functional but aging or visibly worn |
| 1 | Poor | Needs repair or replacement soon |
| 0 | Failed | Not functional or causing damage/risk |

## Quick Room Condition Section

These are the fast pass fields. The inspector should be able to complete this section in 2-3 minutes.

### Entry Door

| Field | Type | Options |
|---|---|---|
| entry_door_condition | score | 0-4 |
| weatherstripping_condition | score | 0-4 |
| lockset_condition | score | 0-4 |
| door_closer_working | boolean | yes/no |
| entry_door_notes | long_text | optional |

### Walls

| Field | Type | Options |
|---|---|---|
| wall_condition | score | 0-4 |
| wall_scuffs | select | none/minor/major |
| drywall_damage | boolean | yes/no |
| wall_water_damage | boolean | yes/no |
| paint_needed | select | no/spot/full |
| wall_notes | long_text | optional |

### Ceiling

| Field | Type | Options |
|---|---|---|
| ceiling_condition | score | 0-4 |
| ceiling_water_stains | boolean | yes/no |
| ceiling_sagging | boolean | yes/no |
| ceiling_repair_needed | boolean | yes/no |
| ceiling_notes | long_text | optional |

### Floor

| Field | Type | Options |
|---|---|---|
| floor_type | select | carpet/lvp/tile/other |
| floor_condition | score | 0-4 |
| floor_water_damage | boolean | yes/no |
| floor_soft_spots | boolean | yes/no |
| floor_trip_hazard | boolean | yes/no |
| floor_replacement_needed | boolean | yes/no |
| floor_notes | long_text | optional |

### Mirror

| Field | Type | Options |
|---|---|---|
| mirror_condition | score | 0-4 |
| mirror_cracked | boolean | yes/no |
| mirror_loose | boolean | yes/no |
| mirror_replacement_needed | boolean | yes/no |
| mirror_notes | long_text | optional |

### Window

| Field | Type | Options |
|---|---|---|
| window_glass_condition | score | 0-4 |
| screen_condition | select | good/damaged/missing |
| window_lock_working | boolean | yes/no |
| window_caulking_condition | score | 0-4 |
| window_water_intrusion | boolean | yes/no |
| window_notes | long_text | optional |

## PTAC Quick Section

| Field | Type | Options |
|---|---|---|
| ptac_present | boolean | yes/no |
| ptac_ac_works | boolean | yes/no |
| ptac_heat_works | boolean | yes/no |
| ptac_dry_mode_works | boolean | yes/no/unknown |
| ptac_fan_works | boolean | yes/no |
| ptac_noise | select | normal/excessive |
| ptac_filter_condition | select | clean/dirty/missing |
| ptac_coils_need_cleaning | boolean | yes/no |
| ptac_condensate_drain | select | clear/restricted/unknown |
| ptac_water_intrusion | boolean | yes/no |
| ptac_notes | long_text | optional |

## PTAC Expanded Asset Section

Open this only when more detailed information is needed.

Creates or updates an asset record where asset_type = `ptac`.

| Field | Type | Notes |
|---|---|---|
| ptac_manufacturer | text | optional |
| ptac_model | text | optional |
| ptac_serial | text | optional |
| ptac_voltage | text | optional |
| ptac_btu | text | optional |
| ptac_age_estimate | text | optional |
| ptac_drain_pan_condition | score | 0-4 |
| ptac_sleeve_condition | score | 0-4 |
| ptac_interior_seal_condition | score | 0-4 |
| ptac_exterior_seal_condition | score | 0-4 |
| ptac_wall_penetration_sealed | boolean | yes/no |
| ptac_floor_damage_around_unit | boolean | yes/no |
| ptac_wall_damage_around_unit | boolean | yes/no |
| ptac_recommended_action | select | clean/service/repair/replace/monitor |

## Bathroom Quick Section

| Field | Type | Options |
|---|---|---|
| bathroom_overall_condition | score | 0-4 |
| tub_shower_condition | score | 0-4 |
| tile_condition | score | 0-4 |
| grout_condition | score | 0-4 |
| shower_caulk_condition | score | 0-4 |
| bathroom_water_intrusion | boolean | yes/no |
| toilet_secure | boolean | yes/no |
| toilet_base_caulking | score | 0-4 |
| sink_condition | score | 0-4 |
| sink_drain_gasket_condition | score | 0-4 |
| vanity_condition | score | 0-4 |
| exhaust_fan_operational | boolean | yes/no |
| bathroom_notes | long_text | optional |

## Bathroom Expanded Asset Section

Open this when fixture inventory or deeper repair details are needed.

### Shower / Tub Asset

Creates or updates an asset record where asset_type = `shower_valve` or `tub_shower`.

| Field | Type | Notes |
|---|---|---|
| shower_manufacturer | text | Delta/Moen/Kohler/etc. |
| shower_model | text | optional |
| shower_cartridge_number | text | optional |
| shower_valve_type | text | optional |
| shower_head_condition | score | 0-4 |
| temperature_control_condition | score | 0-4 |
| missing_tile | boolean | yes/no |
| loose_tile | boolean | yes/no |
| tub_cracked | boolean | yes/no |
| shower_recommended_action | select | recaulk/repair cartridge/replace fixture/tile repair/monitor |

### Toilet Asset

Creates or updates an asset record where asset_type = `toilet`.

| Field | Type | Notes |
|---|---|---|
| toilet_manufacturer | text | optional |
| toilet_model | text | optional |
| toilet_flush_condition | score | 0-4 |
| toilet_fill_valve_condition | score | 0-4 |
| toilet_flapper_condition | score | 0-4 |
| wax_ring_suspected_failure | boolean | yes/no |
| toilet_recommended_action | select | service/reset/recaulk/replace/monitor |

### Sink / Faucet Asset

Creates or updates an asset record where asset_type = `sink_faucet` or `lavatory_sink`.

| Field | Type | Notes |
|---|---|---|
| sink_manufacturer | text | optional |
| sink_model | text | optional |
| faucet_type | text | single handle/two handle/other |
| faucet_cartridge_number | text | optional |
| drain_assembly_condition | score | 0-4 |
| popup_assembly_working | boolean | yes/no |
| supply_stops_condition | score | 0-4 |
| supply_lines_condition | score | 0-4 |
| sink_recommended_action | select | service/replace gasket/replace faucet/replace sink/monitor |

### Exhaust Fan Asset

Creates or updates an asset record where asset_type = `bath_exhaust_fan`.

| Field | Type | Notes |
|---|---|---|
| exhaust_fan_manufacturer | text | optional |
| exhaust_fan_model | text | optional |
| exhaust_fan_noise | select | normal/excessive |
| exhaust_fan_recommended_action | select | clean/repair/replace/monitor |

## Electrical Quick Section

| Field | Type | Options |
|---|---|---|
| lights_working | boolean | yes/no |
| outlets_condition | score | 0-4 |
| gfci_working | boolean | yes/no/unknown |
| electrical_notes | long_text | optional |

## Photos Section

Photos may be attached to:

- inspection
- room
- asset
- deficiency

| Field | Type | Required | Notes |
|---|---|---:|---|
| photo | image | yes | Camera upload |
| caption | text | no | Example: PTAC leak at left side |
| linked_category | select | no | PTAC/bathroom/floor/wall/etc. |
| linked_deficiency_code | select | no | Optional deficiency link |

## Deficiencies Section

The inspector can add deficiencies manually or the app can suggest them from answers.

Example auto-suggestions:

| Trigger | Suggested Code |
|---|---|
| ptac_coils_need_cleaning = yes | PTAC-002 |
| ptac_water_intrusion = yes | PTAC-008 |
| toilet_base_caulking score <= 1 | BATH-002 |
| sink_drain_gasket_condition score <= 1 | PLMB-002 |
| ceiling_water_stains = yes | CEIL-001 |
| floor_trip_hazard = yes | FLR-004 |
| window_water_intrusion = yes | WIN-005 |
| gfci_working = no | ELEC-003 |

Deficiency fields:

| Field | Type | Required |
|---|---|---:|
| code | select | yes |
| category | select | yes |
| description | text | yes |
| severity | select | yes |
| estimated_cost | money | no |
| status | select | yes |
| notes | long_text | no |

## Cost Estimate Section

| Field | Type |
|---|---|
| paint_estimate | money |
| ptac_estimate | money |
| bathroom_estimate | money |
| flooring_estimate | money |
| electrical_estimate | money |
| other_estimate | money |
| estimated_total_cost | calculated money |

## Save Behavior

When the user taps Save:

1. Create inspection record.
2. Create inspection_items from quick fields.
3. Create or update expanded assets if opened.
4. Create deficiencies from selected or suggested codes.
5. Upload photos to storage.
6. Link photos to inspection/assets/deficiencies.
7. Recalculate room score.
8. Return to room dashboard.

## V1 Design Rule

The form must be usable one-handed on Android.

Default fields should be fast.
Expanded fields should be optional.
Photos should be easy.
Notes should never block saving.

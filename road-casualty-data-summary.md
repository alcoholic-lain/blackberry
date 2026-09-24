# UK Road Casualty Data Summary

This workspace contains three related CSV tables from the UK Department for Transport road casualty statistics. Together they describe collisions, the vehicles involved, and the resulting casualties.

## Table Specifications

| Table | Specification | Grain | Fields |
|---|---|---|---:|
| Collision | [collision-data-spec.md](collision-data-spec.md) | One row per collision | 44 |
| Vehicle | [vehicle-data-spec.md](vehicle-data-spec.md) | One row per vehicle | 32 |
| Casualty | [casualty-data-spec.md](casualty-data-spec.md) | One row per casualty | 23 |

## Relationships

```text
Collision
  ├── Vehicle: collision_index + vehicle_reference
  └── Casualty: collision_index + casualty_reference
```

- `collision_index` links records in all three tables to the same collision.
- `collision_ref_no` is an additional collision reference present in each table.
- `vehicle_reference` identifies a vehicle within a collision.
- `casualty_reference` identifies a casualty within a collision.
- A casualty's `vehicle_reference` can link that casualty to the relevant vehicle where applicable.

## Shared Data Rules

- The files are CSVs with one header row.
- Preserve identifiers and codes as strings so leading zeroes are not lost.
- `-1` and blank values commonly represent unavailable, unknown, or not-applicable values.
- Do not treat `-1` as numeric zero.
- Most categorical values are numeric codes and require the official DfT data dictionary for interpretation.
- Collision dates are observed in `DD/MM/YYYY` format and times in 24-hour `HH:MM` format.
- Adjusted severity fields can contain decimal proportions.

## Recommended Join Order

1. Load the collision table as the parent table.
2. Join vehicles using `collision_index`.
3. Join casualties using `collision_index`.
4. Where vehicle-level casualty analysis is needed, also match casualty `vehicle_reference` to vehicle `vehicle_reference` within the same `collision_index`.

See the individual specifications for the complete field-by-field explanations and validation rules.
# Casualty Table Field Specification

**CSV:** `dft-road-casualty-statistics-casualty-1979-latest-published-year.csv`  
**Grain:** One row per casualty in a collision. **Columns:** 23.

`-1` and blank values generally mean unavailable, unknown, or not applicable. Numeric category fields are codes; use the official DfT lookup tables for their exact meanings.

| Field | Explanation |
|---|---|
| `collision_index` | Collision identifier linking the casualty to a collision record. |
| `collision_year` | Year in which the collision occurred. |
| `collision_ref_no` | Collision reference number supplied in the source data. |
| `vehicle_reference` | Vehicle number associated with the casualty where applicable. |
| `casualty_reference` | Casualty number within the collision; paired with `collision_index` to identify a casualty. |
| `casualty_class` | Coded role or class of the casualty, such as driver, passenger, or pedestrian. |
| `sex_of_casualty` | Coded sex of the casualty. |
| `age_of_casualty` | Casualty age in years where recorded. |
| `age_band_of_casualty` | Coded age group for the casualty. |
| `casualty_severity` | Original coded severity of the casualty's injury. |
| `pedestrian_location` | Coded location of a pedestrian in relation to the road. |
| `pedestrian_movement` | Coded movement of a pedestrian immediately before the collision. |
| `car_passenger` | Coded indicator describing the casualty's position as a car passenger. |
| `bus_or_coach_passenger` | Coded indicator describing the casualty's position as a bus or coach passenger. |
| `pedestrian_road_maintenance_worker` | Coded indicator identifying a pedestrian road-maintenance worker. |
| `casualty_type` | Coded type of casualty or road user. |
| `casualty_imd_decile` | Casualty's area deprivation decile based on the Index of Multiple Deprivation. |
| `lsoa_of_casualty` | Lower-layer Super Output Area associated with the casualty. |
| `enhanced_casualty_severity` | Enhanced or revised coded casualty severity measure. |
| `casualty_injury_based` | Coded indicator or classification based on the casualty's injury. |
| `casualty_adjusted_severity_serious` | Adjusted serious-severity estimate or proportion. |
| `casualty_adjusted_severity_slight` | Adjusted slight-severity estimate or proportion. |
| `casualty_distance_banding` | Coded band for the casualty's travel distance. |

## Validation

- Keep `collision_index`, `collision_ref_no`, `vehicle_reference`, and `casualty_reference` as strings.
- Check uniqueness of `(collision_index, casualty_reference)`.
- Check that each collision link exists before joining to the collision table.
- Treat `-1` as a code, not as a numeric zero.
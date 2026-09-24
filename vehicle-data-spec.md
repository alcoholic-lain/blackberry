# Vehicle Table Field Specification

**CSV:** `dft-road-casualty-statistics-vehicle-1979-latest-published-year.csv`  
**Grain:** One row per vehicle involved in a collision. **Columns:** 32.

`-1` and blank values generally mean unavailable, unknown, or not applicable. Numeric category fields are codes; use the official DfT lookup tables for their exact meanings.

| Field | Explanation |
|---|---|
| `collision_index` | Collision identifier linking the vehicle to a collision record. |
| `collision_year` | Year in which the collision occurred. |
| `collision_ref_no` | Collision reference number supplied in the source data. |
| `vehicle_reference` | Vehicle number within the collision; paired with `collision_index` to identify a vehicle. |
| `vehicle_type` | Coded type of vehicle. |
| `towing_and_articulation` | Coded information about towing, trailers, or articulated vehicles. |
| `vehicle_manoeuvre_historic` | Historic coded vehicle manoeuvre before or during the collision. |
| `vehicle_manoeuvre` | Current coded vehicle manoeuvre before or during the collision. |
| `vehicle_direction_from` | Coded direction from which the vehicle approached. |
| `vehicle_direction_to` | Coded direction toward which the vehicle was travelling. |
| `vehicle_location_restricted_lane_historic` | Historic code for the vehicle's restricted-lane location. |
| `vehicle_location_restricted_lane` | Current code for the vehicle's restricted-lane location. |
| `junction_location` | Coded position of the vehicle in relation to a junction. |
| `skidding_and_overturning` | Coded indication of skidding, overturning, or neither. |
| `hit_object_in_carriageway` | Coded object in the carriageway hit by the vehicle. |
| `vehicle_leaving_carriageway` | Coded indication of whether the vehicle left the carriageway. |
| `hit_object_off_carriageway` | Coded object off the carriageway hit by the vehicle. |
| `first_point_of_impact` | Coded first point on the vehicle that was impacted. |
| `vehicle_left_hand_drive` | Coded indicator of left-hand-drive configuration. |
| `journey_purpose_of_driver_historic` | Historic coded purpose of the driver's journey. |
| `journey_purpose_of_driver` | Current coded purpose of the driver's journey. |
| `sex_of_driver` | Coded sex of the driver. |
| `age_of_driver` | Driver age in years where recorded. |
| `age_band_of_driver` | Coded age group for the driver. |
| `engine_capacity_cc` | Engine capacity in cubic centimetres where applicable. |
| `propulsion_code` | Coded propulsion or fuel type. |
| `age_of_vehicle` | Age of the vehicle, generally in years, where recorded. |
| `generic_make_model` | Text description of the vehicle make and model. |
| `driver_imd_decile` | Driver's area deprivation decile based on the Index of Multiple Deprivation. |
| `lsoa_of_driver` | Lower-layer Super Output Area associated with the driver. |
| `escooter_flag` | Coded indicator identifying an electric scooter. |
| `driver_distance_banding` | Coded band for the driver's journey distance. |

## Validation

- Keep `collision_index`, `collision_ref_no`, and `vehicle_reference` as strings.
- Check uniqueness of `(collision_index, vehicle_reference)`.
- Check that each collision link exists before joining to the collision table.
# Collision Table Field Specification

**CSV:** `dft-road-casualty-statistics-collision-1979-latest-published-year.csv`  
**Grain:** One row per road collision. **Columns:** 44.

`-1` and blank values generally mean unavailable, unknown, or not applicable. Numeric category fields are codes; use the official DfT lookup tables for their exact meanings.

| Field | Explanation |
|---|---|
| `collision_index` | Unique collision identifier used to link this table to vehicle and casualty records. |
| `collision_year` | Year in which the collision occurred. |
| `collision_ref_no` | Collision reference number supplied in the source data. |
| `location_easting_osgr` | Ordnance Survey grid easting coordinate for the collision location. |
| `location_northing_osgr` | Ordnance Survey grid northing coordinate for the collision location. |
| `longitude` | Geographic longitude; may be blank for older records. |
| `latitude` | Geographic latitude; may be blank for older records. |
| `police_force` | Code for the police force responsible for the area. |
| `collision_severity` | Original coded severity classification of the collision. |
| `number_of_vehicles` | Number of vehicles involved in the collision. |
| `number_of_casualties` | Number of casualties recorded for the collision. |
| `date` | Collision date, observed in `DD/MM/YYYY` format. |
| `day_of_week` | Coded day of the week on which the collision occurred. |
| `time` | Collision time, observed in 24-hour `HH:MM` format. |
| `local_authority_district` | Numeric code for the local authority district. |
| `local_authority_ons_district` | ONS code for the local authority district. |
| `local_authority_highway` | Code for the highway authority. |
| `local_authority_highway_current` | Current highway authority code used by the source. |
| `first_road_class` | Coded class of the first or main road at the collision. |
| `first_road_number` | Number identifying the first or main road. |
| `road_type` | Coded type of the road at the collision. |
| `speed_limit` | Posted speed limit, normally in miles per hour. |
| `junction_detail_historic` | Historic coded description of the junction layout. |
| `junction_detail` | Current coded description of the junction layout. |
| `junction_control` | Coded type of control at the junction. |
| `second_road_class` | Coded class of the second road at the junction. |
| `second_road_number` | Number identifying the second road. |
| `pedestrian_crossing_human_control_historic` | Historic code for human control at a pedestrian crossing. |
| `pedestrian_crossing_physical_facilities_historic` | Historic code for physical pedestrian-crossing facilities. |
| `pedestrian_crossing` | Current coded pedestrian-crossing type or facility. |
| `light_conditions` | Coded lighting conditions when the collision occurred. |
| `weather_conditions` | Coded weather conditions when the collision occurred. |
| `road_surface_conditions` | Coded condition of the road surface. |
| `special_conditions_at_site` | Coded special conditions at the collision site. |
| `carriageway_hazards_historic` | Historic coded hazard affecting the carriageway. |
| `carriageway_hazards` | Current coded hazard affecting the carriageway. |
| `urban_or_rural_area` | Coded classification of the location as urban or rural. |
| `did_police_officer_attend_scene_of_accident` | Coded indicator of whether police attended the scene. |
| `trunk_road_flag` | Coded indicator of whether the road was a trunk road. |
| `lsoa_of_accident_location` | Lower-layer Super Output Area code for the collision location. |
| `enhanced_severity_collision` | Enhanced or revised coded collision severity measure. |
| `collision_injury_based` | Coded indicator or classification based on injury involvement. |
| `collision_adjusted_severity_serious` | Adjusted serious-severity estimate or proportion. |
| `collision_adjusted_severity_slight` | Adjusted slight-severity estimate or proportion. |

## Validation

- Keep identifiers and codes as strings until missing values have been handled.
- Parse `date` as `DD/MM/YYYY` and `time` as `HH:MM`.
- Check that vehicle and casualty `collision_index` values can be matched when joining tables.
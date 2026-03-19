# Proximity Scripts

This repo contains python scripts (described below) and sample data to perform proximity analysis using the [betweenPairs](https://openapi.apps.gov.bc.ca/?url=https://raw.githubusercontent.com/bcgov/api-specs/master/router/router.json#/distance/get_distance_betweenPairs__outputFormat) endpoint of the [BC Route Planner](https://www2.gov.bc.ca/gov/content?id=9D99E684CCD042CD88FADC51E079B4B5).

- **1_dist_time_to_nearest_destination.py:** Use the [BC Route Planner](https://www2.gov.bc.ca/gov/content?id=9D99E684CCD042CD88FADC51E079B4B5) to determine distance and drive time from each origin point to the nearest destination point **(figure 1)**.

- **1_dist_time_to_nearest_destination_with_admin_area.py:** Use the [BC Route Planner](https://www2.gov.bc.ca/gov/content?id=9D99E684CCD042CD88FADC51E079B4B5) to determine distance and drive time from each origin point to the nearest destination point **AND** include an administrative area ID field in the output **(figure 1)**.
  
- **1b_route_salvager_with_admin_area.py:** Use the [BC Route Planner](https://www2.gov.bc.ca/gov/content?id=9D99E684CCD042CD88FADC51E079B4B5) to provide a new random sample of addresses to replace those that were unroutable using the 1_dist_time_to_nearest_destination_with_admin_area.py script. This list of replacement addresses can then be reprocessed by the 1_dist_time_to_nearest_destination_with_admin_area.py script and replace the records containing NULL values in the original output **(figure 2)**.
  
- **2_avg_dist_time_per_destination.py:** Use the [BC Route Planner](https://www2.gov.bc.ca/gov/content?id=9D99E684CCD042CD88FADC51E079B4B5) to calculate average distance and drive time for each destination point using all nearest origin points (**figure 3**).

- **2_avg_dist_time_per_destination_no_routing.py:** Calculate average distance and drive time for each destination point using all nearest origin points, via summary statistics (no routing involved). This script is recommended if you used the BC Route Planner to create the CSV of nearest origin points (by previously running 1_dist_time_to_nearest_destination.py or 1_dist_time_to_nearest_destination_with_admin_area.py).
- *Sample input arguments included at the top of each script.*
- *BC Route Planner API parameter defaults are listed [here.](https://github.com/BK01/proximity-by-road/blob/main/parameter_default_values.md)*

# third-party libraries

The python scripts listed above require the installation of the following third-party libraries.
- pandas
- requests
- retry


# Process Overview
![image](https://github.com/user-attachments/assets/2e186f26-ca62-4a07-9c91-adabd3153df6)
<img width="975" height="342" alt="399525015-2e186f26-ca62-4a07-9c91-adabd3153df6_v2" src="https://github.com/user-attachments/assets/98b30b18-30bb-4252-b312-f20cd3f1bc6e" />


**Figure 1:** Determine the nearest destination point to each origin point based on drive time (1_dist_time_to_nearest_destination.py).

![route_salvager](https://github.com/user-attachments/assets/7a90a0c1-b04b-4f05-933f-5f664749a07b)
<img width="822" height="442" alt="425550300-7a90a0c1-b04b-4f05-933f-5f664749a07b_v2" src="https://github.com/user-attachments/assets/576a30d8-f8fa-4e13-819e-5ce6add0e3b7" />


**Figure 2:** If processing a sample of a larger dataset, this script can be used to replace unroutable coordinates with routable coordinates (1b_route_salvager_with_admin_area.py).

![avg_dist_2](https://github.com/user-attachments/assets/753461cd-cb21-4b9c-ada9-58232ad98432)
<img width="412" height="442" alt="425553000-753461cd-cb21-4b9c-ada9-58232ad98432_v2" src="https://github.com/user-attachments/assets/f80fe6c2-9c2f-401f-aafa-60bac7365444" />


**Figure 3:** Calculate average distance and drive time to each destination point using all nearest origin points (2_avg_dist_time_per_destination.py)

# API key request form:
**The BC Route Planner is currently only available for use by B.C. Government Ministries.**
https://dpdd.atlassian.net/servicedesk/customer/portal/1/group/7/create/9

 Note: use [mknotebooks](https://github.com/greenape/mknotebooks) to integrate notebooks with MkDocs, or download final notebook as markdown file (note that output cells will be treated as their own code block).

## Research Questions

1. What amount of ecosystem services (species habitat, water benefits) can be accrued under the business as usual case?
2. What amount of ecosystem services could be acquired with augmented budgets?

## Approach

### 1. Setup

**Input:** 

For each PPIC region (e.g., Kern County), a table of fields as records and features including crop type, size in acres, and ecosystem services features (e.g., suitability-weighted acreage of individual species habitat).

**Feature engineering:** 

- Features that aggregate the ecosystem services must be calculated to facilitate the greedy algorithm. Multiple scenarios can be run (e.g., most habitat, most water recharge), but the 'optimal' solution needs a single ecosystem service feature to optimize for. Weightings and aggregation approach must be proposed.
- Crop types must be modified to match the PPIC crop type categories. A cross-reference table must be built.

### 2. Business as usual case

To begin, we must understand the business as usual case. Use a bootstrap approach to model a distribution of potential ecosystem service outcomes (i.e., amount of ecosystem services acquired). This will provide baseline for probabilistic comparison of the optimal outcome (i.e., if left to chance, what is the probability we would get 90% of the ecosystem services acquired through strategic acquisistion?).

1. For each crop type, select random fields until the acreage target is hit.
2. Store the field ID in a list
3. Sum the ecosystem service values for each field acquired in a value store for each ecosystem service (including aggregate features)
4. Repeat 1,000 iterations and store outcomes of each iteration in a unique list of outcomes for each ecosystem service (including aggregate features); store the list of field IDs in a table (append n/a as field ID list will be variable length)

### 3. Strategic acquisition

1. For each crop type, sort the table based on the aggregate ecosystem service feature or ecosystem service of interest
2. Acquire fields in order until acreage target for the crop type is satisfied
3. Store the field ID in a list
4. Sum the ecosystem service values for each field acquired in a value store for each ecosystem service (including aggregate features)
5. Repeat with additional ecosystem services as desired.

### 4. Budget augmentation

TBD

## Outputs

The business as usual case can be visualized as a histogram of the bootstrap attempts and the outcome in terms of the top-tier aggregate ecosystem service output. Include a pointer for the strategic acquisition optimum and the 90% of optimum solution. This will illustrate the distance between the business as usual and optimal outcomes with some acknowledgement that the optimum is unlikely due to landowner preferences, network effects, etc.

The strategic acquisition case can be visualized spatially. Display a map of the acquired fields and some visualization of the ecosystems services provided.

A final report with figures will be provided in pdf and the notebook associated will be included as some shareable format.

## Data

The crop acreage fallowing targets are as shown in Table 1.

**Table 1**

|      | Alfalfa & Pasture | Corn  | Other field crops and grains | Vegetables & non-tree fruits | Trees & vines |
| :----: | :-------------------: | :-----: | :------------------------------: | :------------------------------: | :---------------: |
| NW   | 21.32               | 8.40  | 85.92                          | 3.88                           | 3.88            |
| NE   | 56.85               | 7.75  | 23.58                          | 2.26                           | 16.80           |
| SW   | 36.82               | 3.88  | 72.35                          | 8.40                           | 7.75            |
| SE   | 38.76               | 16.15 | 124.03                         | 0.65                           | 9.69            |
| KR   | 88.50               | 54.91 | 42.64                          | 3.23                           | 11.63           |

*Thousands of acres
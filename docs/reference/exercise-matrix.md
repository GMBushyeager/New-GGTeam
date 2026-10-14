# Fitness assessment exercises by assessment type

Source: `Fitness Assessment SteUp.xlsx` (Gregg's OneDrive, last modified March 5, 2025),
sheet `FITNESS`. Numbers are the display order within each assessment type. A blank
cell means the exercise isn't part of that type.

The Mongo key column maps each spreadsheet row to the production field under
`fitnessAssessment.program` or `fitnessAssessment.test`. Keys are copied exactly
from `prod.assessments`.

## Program exercises (`fitnessAssessment.program.<key>`)

Each one stores `bandCompany`, `colourBand`, `colourName`, `observation[]`, `other`
and `score` (`None`, `Poor`, `Fair`, `Good`, `Excellent`).

| Exercise (display name) | Category | Adult | Youth | Senior | Adaptive | Mongo key |
|---|---|---|---|---|---|---|
| Squat | Quad | 1 | 1 | | 1 | `squats` |
| Shoulder Press | Shoulder | 2 | 2 | 2 | | `shoulderPress` |
| Plank | Abs | 3 | 3 | 3 | 7 | `plank` |
| High Knees | Cardio | 4 | 4 | 4 | | `highKnees` |
| Lateral Kicks | Glute | 5 | | | | `lateralKicks` |
| Standing Row | Back | 6 | 6 | | | `standingRow` |
| Side Plank R/L | Abs | 7 | 7 | | | `sidePlankRL` |
| Skaters | Cardio | 8 | | | | `skaters` |
| Forward Bend | ROM | 9 | 9 | 8 | 9 | `forwardBend` |
| Single Leg Balance - Right | Stability | 10 | 10 | 9 | 10 | `singleLegBalanceRight` |
| Single Leg Balance - Left | Stability | 11 | 11 | 10 | 11 | `singleLegBalanceLeft` |
| Bear Crawl | Abs | | 5 | | | `bearCrawl` |
| Agility Ladder | Cardio | | 8 | | | `agilityLadder` |
| Squat / Sit 2 Stand | Quad | | | 1 | | `squatSitToStand` |
| Gait | ROM | | | 5 | | `gait` |
| Floor - Down & Up | ROM | | | 6 | | `floorDownUp` |
| Side-Step | ROM | | | 7 | | `sideStep` |
| Overhead Reach | Shoulder | | | | 2 | `overHeadReach` |
| Standing Cross Crunch | Abs | | | | 3 | `standingCrossCrunch` |
| Shuffle | ROM | | | | 4 | `shuffle` |
| Lateral & Posterior Kicks | Glute | | | | 5 | `lateralAndPosteriorKicks` |
| Push Up | Chest | | | | 6 | `pushUp` |
| Jumping Jacks | Cardio | | | | 8 | `jumpingJacks` |
| **Count** | | **11** | **11** | **10** | **11** | |

## Timed tests (`fitnessAssessment.test.<key>`)

Each one stores `reps` and `timing` (seconds, as a string). Some also store
`observation[]` and `other`.

| Test (display name) | Adult | Youth | Senior | Adaptive | Mongo key |
|---|---|---|---|---|---|
| S2S Endurance Jump | 1 | 1 | | | `s2sEnduranceJump` |
| Push Up | 2 | 2 | | | `pushUp` |
| Squat Jump | 3 | | | | `squatJump` |
| Frog Jump | | 3 | | | `frogJump` |
| Plank / Shoulder Touch | 4 | 4 | | | `plankOrShoulderTouch` |
| Step Test | | | 1 | | `stepTest` |
| Dominant Seated Arm Curl | | | 2 | | `dominantSeatedArmCurl` |
| Elevated Push Up | | | 3 | | `elevatedPushUp` |
| Chair Sit 2 Stand | | | 4 | | `chairSitToStand` |
| Lateral Jump | | | | 1 | `lateralJump` |
| Alternate Heal Touch | | | | 2 | `alternateHealTouch` |
| Sit To Stand | | | | 3 | `sitToStand` |
| Big Arm Circles | | | | 4 | `bigArmCircles` |

`pushUp` is a key under both `program` and `test`. Adaptive uses it as a program
exercise, while Adult and Youth use it as a timed test.

## How this compares with production

Checked against all 4,877 documents in `prod.assessments`:

- **Older documents store only the type's own set.** Examples are the 433 Adult
  documents with 11 exercises and 4 tests, and the 124 Senior documents with 10
  exercises and 4 tests. These sets match the columns above exactly.
- **Newer documents store all 23 exercises and 13 tests** whatever the type. The
  ones that aren't part of the type keep defaults (empty, or a score of `None`).
  When you count only exercises with a real score or an observation, each type's
  filled set matches its column. For example, Adult documents have scores for
  `squats` (88%), `plank` (82%) and `shoulderPress` (82%), and 2% or less for
  anything outside the Adult column.
- **Some exercises outside the matrix get filled for a small share of documents:**
  Youth `lateralKicks` (11%) and `skaters` (9%), Senior `squats` (9%), and Adaptive
  `shoulderPress` (11%) and `highKnees` (9%). This may happen when a trainer changes
  the assessment type partway through, but that isn't confirmed.

## Notes and open questions

From the sheet itself:

- The header notes say "Nothing sent to summary". They also ask "Do we use bands on
  all exercises?" and "Do we [have] form videos to show client?" (noted for Heidi).
- The `ASSESS / REEASS FLAG` column is empty for every row. That leaves it
  unclear whether a reassessment uses the same exercises as the initial
  assessment.

Open questions:

1. **(Gregg)** Does a reassessment always use the same exercise set as the initial
   assessment of its type? Or can the trainer change it, or switch the client's
   type?
2. **(Gregg)** Should the new app write only the type's own exercises, as older
   documents did, or keep writing all 23 and 13 with defaults? Either way parses
   against production, but downstream Snowflake logic may expect one or the other.
3. **(Gregg)** Should the 9–11% of out-of-matrix scores (see above) be treated as
   valid data or as noise?
4. **(Gregg)** Should every type use bands, or only some exercises? `bandCompany`
   is also stored once at the top level as `fitnessAssessment.bandCompany`.

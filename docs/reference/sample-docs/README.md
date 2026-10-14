# Sample documents

Redacted `prod.assessments` documents, plus a field inventory built from the
full production export (4,877 documents, January 6, 2025 through October 14, 2026).
The export itself is **not** in the repo.

- `field-inventory.md` lists every field path with its type, its document count and,
  for closed-list fields, every stored option value.
- The `*.json` files are single documents in MongoDB Extended JSON.

## Samples

All four assessment types are covered, each with an initial assessment and a
reassessment of the **same client**. Each pair shares a placeholder `clientPk`.

| File | `assessmentType` | `isReassessment` | `assessmentCount` | Why it's here |
|---|---|---|---|---|
| `adult-initial.json` | Adult | false | 1 | Complete initial assessment |
| `adult-reassessment.json` | Adult | true | 2 | Same client; has a `reassessmentComments` entry |
| `senior-initial.json` | Senior | false | 1 | Complete initial assessment |
| `senior-reassessment.json` | Senior | true | 2 | Same client; both `reassessmentComments` filled |
| `youth-initial.json` | Youth | false | 1 | Complete initial assessment |
| `youth-reassessment.json` | Youth | true | 2 | Same client; has a `reassessmentComments` entry |
| `adaptive-initial.json` | Adaptive | false | 1 | Complete initial with `adaptiveReport` filled |
| `adaptive-reassessment.json` | Adaptive | true | 2 | Same client |
| `with-history.json` | Adult | false | 1 | Non-empty `assestmentHistory` |
| `partial-parq-only.json` | Adult | true | 4 | PARQ saved, later sections not filled |
| `legacy-no-program.json` | Senior | (missing) | 2 | Older document: no `isReassessment`, no `fitnessAssessment.program` |

## How these were redacted

Every field name, the nesting, key order, value types, array lengths and empty
strings are kept exactly as they are in production. Values are handled like this:

- **Kept:** option values picked from closed lists (array elements, `score`,
  `bandCompany`, `colourName`, `colourBand`, `timing`, `assessmentType`, `Gender`,
  `appVersion`), booleans, rep counts and other counters.
- **Replaced with fixed placeholders:** everything in `mindBodyData`, the caregiver
  name and contact, `mboTrainerName`, every Mindbody ID, `clientPk`, `trainerPk`,
  `_id`, `assestmentHistory` IDs, device and OS info, every date and timestamp,
  and the body measurements and goal weight. These keep the production format,
  for example `"5'10\""` and `"180.0"` as strings.
- **Replaced with `"[redacted]"`:** every free-text value, including the `*Other`
  fields, comments, the adaptive questionnaire text and `finishAssessmentPrompt*`.

A script checked that no original string of four or more characters survives
in any sample.

## What the export shows

These are facts from the data. Items that need a decision are marked **(Gregg)**.

1. **Every assessment holds a full copy of the client's Mindbody record**
   (`mindBodyData`): name, birth date, email, mobile phone, address and emergency
   contact. **(Gregg)** Should the new app keep copying this into each assessment,
   or store only `mboClientId` and look the rest up? This touches health-data
   retention, which is on the stop-and-ask list.
2. **Most body measurements are strings:** `weightInLBS`, `height` (`5'10"`),
   `bodyAge`, `bodyFatPercentage`, `bodyMassIndex` and `muscleMassPercentage`.
   About 1,100–1,600 documents have them empty. `ageInYears`, `visceralFat` and the
   girth fields are numbers. The new schema has to accept the strings.
3. **Dates use several string formats:** `physicalDate` and `dueDate` are
   `MM-DD-YYYY`, `smokeQuitDate` is `MM/YYYY`, and `BirthDate` is mostly
   `MM-DD-YYYY` with a few `YYYY-MM-DD`. `trainStarTime` (spelled that way in
   production) is `07 :00 AM` with a stray space in 2,754 documents, and some
   documents store the empty picker value `--:-- --`.
4. **`clientCommunicationMode` appends instead of replacing.** It is a string,
   and 46 documents hold values such as `IndependentlyBoth`. In the screens it's
   a single choice.
5. **The same option is stored with different spellings:** `1 – 2` vs `1 - 2`
   (en dash) in alcohol and exercise, `Grey` vs `Gray`, `Out of Breath` vs
   `Out Of Breath`, and leading spaces in ` Excessive Forward Lean` and
   ` Poor ROM`. Derived values that compare labels will need to normalize them.
6. **`assestmentHistory` points somewhere else.** 120 documents hold 288 IDs, and
   none of them match an `_id` in `prod.assessments`. **(Gregg)** Which collection
   do these IDs reference?
7. **Reassessment markers:** `isReassessment` is missing from 969 documents, all
   created on or before June 24, 2025. `assessmentCount` is present on every
   document. `reassessmentComments` holds only `bodyAssessmentComment` and
   `fitnessAssessmentComment`.
8. **All exercises are stored whatever the assessment type.** Most documents have
   all 23 `program` exercises and all 13 `test` entries, so the assessment type
   doesn't decide which exercises are stored. 865 documents, including recent
   ones, have no `program` at all. 433 Adult documents have an older 11-exercise
   set with 4 tests.
9. **Fields that look unused or duplicated:** `formsFilled` is always 0.
   `ptAgreement` is always `""`, but `isPtAgreementFilled` is true in 4,740
   documents. `toAssessor` and `toTheAssessor` disagree in 949 documents.
   `comments` is missing from 996 documents.
10. **135 documents look like test data:** a negative `mboSiteId` and
    `GG-`/`GGT-` IDs. **(Gregg)** Confirm these can be excluded from parity checks.
11. **Some field names don't match the screen labels:** "Other Conditions" is
    stored in `parq.medicalHistory.physical[]`, the "Physical" yes/no question in
    `havePhysicalRecently`, and "Other Medications" in `medications[]`.
    `colourBand`/`colourName` use British spelling. All of these stay as they are.

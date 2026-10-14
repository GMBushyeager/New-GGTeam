# 03 — New assessment

Status: draft

Roles: Trainer, Owner / manager and HQ admin can all start and fill a new assessment.
Per Build Spec §5, a trainer creates and edits their own assessments at their assigned
sites, and owners and HQ can do the same for other trainers. Every field in this flow
is client fitness and health data. None of it is financial, so no field is hidden by
role. Role enforcement depends on flow 01, which is blocked on the sign-in decision.

Current screens: deck `Current_GGTeam_App_Flow.pptx`, slides 1–4, screens 1–50.
Files are in `docs/reference/current-screens/` (`s1-01` through `s4-50`). The deck does
not show the screens before Medical History: client pick, assessment type and
Mindbody data (see Open questions 1–2).

What changes: **parity** for every section and field in the current app (source: the
current Resourcifi app, its screens and `prod.assessments`). There are a few **new**
items from the Build Spec (source: GYMGUYZ, Build Spec v0.1 §4 and §6), listed under
"New fields" and "Behavior". The Resourcifi and Simform scope documents are not in
`docs/reference/vendor-scopes/` yet, so no field is cited to them.

Scope: this flow covers filling one assessment for a client who has already been
chosen, from Medical History through "Save and Submit". Client lookup and the
`mindBodyData` snapshot belong to flow 02. Comments (`comments.*`) belong to flow 04.
The AI brief belongs to flow 05. Reassessment prefill, `reassessmentComments` and
`priorAssessmentId` belong to flow 06. This flow writes the same document shape for
reassessments; flow 06 adds to it.

## Steps

The current app runs these screens in order. Each one ends in "Save and Next", and
the last one ends in "Save and Submit". The section tag "PARQ" shows on steps 1–5.

| # | Section (screen title) | Deck screens | Stored under |
| --- | --- | --- | --- |
| 1 | Medical History | 1–8 | `parq.medicalHistory` |
| 2 | Orthopedic History | 9–18 | `parq.ortho` |
| 3 | Family History | 19–20 | `parq.familyHistory` |
| 4 | Lifestyle | 21–26 | `parq.lifestyle` |
| 5 | Goals / Preferences | 27–28 (slide 2) | `parq.goals` |
| 6 | Body Assessment | 27–29 (slide 3) | `bodyAssessment` |
| 7 | Fitness Assessment | 30–41 | `fitnessAssessment` |
| 8 | Adaptive Questionnaire | 42–48 | `adaptiveReport` |
| 9 | Complete Assessment | 49–50 | `finishAssessmentPrompt*`, `toAssessor`, `toTheAssessor` |

The Build Spec (§4) describes eight steps in a different order: Client, Health,
Joints, Goals and lifestyle, Body, Tests, Movement, Notes. See Open question 3.

## Fields

Conventions used in the tables:

- **Type** is the production type. `string[]` is an array of option labels. Options
  are listed with production spelling, including variants and typos. Variants that
  appear in stored data but not on screen are marked "(data)".
- **Required** shows what the current app marks with a red asterisk. The Build Spec
  says only client, site and type are required to save (Open question 4).
- **None** is exclusive in every multi-select list. In production, `None` never
  appears alongside another option.
- **Other** opens a free-text box saved to the paired `*Other` string.
- **Visible to**: every row is visible to all three roles, scoped to their sites,
  unless it says otherwise.

### 1. Medical History (parity)

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Heart | `parq.medicalHistory.heart` | string[] | Yes | Multi: None, Other, Arteriosclerosis, Bypass, Cardiovascular Disease, Congestive Heart Failure, Coronary Heart Disease, Heart Attack, Stent, Stroke, Surgery, ACE Inhibitor (med), Anticoagulant (med), Aspirin (med), Beta Blocker (med), Diuretics (med), Statin (med) | All roles |
| Heart: other | `parq.medicalHistory.heartOther` | string | When Other | Free text | All roles |
| Pacemaker | `parq.medicalHistory.paceMaker` | string[] | Yes | Multi: None, Other, Implantable Defibrillator, Pacemaker | All roles |
| Pacemaker: other | `parq.medicalHistory.paceMakerOther` | string | When Other | Free text | All roles |
| BP | `parq.medicalHistory.bp` | string[] | Yes | Multi: None, Other, Angioplasty, Hypertension, ACE Inhibitor(med) (no space, as stored), Anticoagulant (med), Aspirin (med), Beta Blocker (med), Calcium Blocker (med), Diuretics (med), Statin (med) | All roles |
| BP: other | `parq.medicalHistory.bpOther` | string | When Other | Free text | All roles |
| Last BP | `parq.medicalHistory.lastBp` | string | No | Free text, placeholder `120/90`. Stored mostly as `120/80`, sometimes `12080` or `120/` | All roles |
| Chest Pain | `parq.medicalHistory.chestPain` | string[] | Yes | Multi: None, Other, Angina, Gastritis, Pericarditis, Reflux, Rib Fracture | All roles |
| Chest Pain: other | `parq.medicalHistory.chestPainOther` | string | When Other | Free text | All roles |
| Metabolic | `parq.medicalHistory.metobolic` | string[] | Yes | Multi: None, Other, Fatty Liver, Graves, Hashimotos, Keto, Kidney, Prediabetes, Renal, Thyroid, Type I Diabetes, Type II Diabetes, Hypothyroidism (med), Hyperthyroidism (med), Insulin (med), Statin (med), Anti-Diabetic (med); variant Anti-diabetic (med) (data) | All roles |
| Metabolic: other | `parq.medicalHistory.metobolicOther` | string | When Other | Free text | All roles |
| Pulmonary | `parq.medicalHistory.pulmonary` | string[] | Yes | Multi: None, Other, COPD, Exercise Induced Asthma, Persistent Asthma, Maintenance Inhaler (med), Rescue Inhaler (med) | All roles |
| Pulmonary: other | `parq.medicalHistory.pulmonaryOther` | string | When Other | Free text | All roles |
| Dizziness | `parq.medicalHistory.dizziness` | string[] | Yes | Multi: None, Other, Dizziness, Fainting, Unexplained Shortness of Breath, Vertigo | All roles |
| Dizziness: other | `parq.medicalHistory.dizzinessOther` | string | When Other | Free text | All roles |
| Cholesterol | `parq.medicalHistory.cholesterol` | string[] | Yes | Multi: None, Other, Angina, Atherosclerosis, High LDL, High Triglycerides, Hypercholesterolemia, ACL Inhibitors (med), CoQ10 (med), Cholesterol Absorption Inhibitors (med), PCSK9 Inhibitors (med), Statins (med) | All roles |
| Cholesterol: other | `parq.medicalHistory.cholesterolOther` | string | When Other | Free text | All roles |
| Overweight | `parq.medicalHistory.overweight` | boolean | No | Yes / No | All roles |
| Pregnant | `parq.medicalHistory.pregnant` | boolean | No | Yes / No | All roles |
| Due date | `parq.medicalHistory.dueDate` | string | Not shown in deck | `MM-DD-YYYY`. Set in 34 of the 35 documents where `pregnant` is true (Open question 5) | All roles |
| Physical | `parq.medicalHistory.havePhysicalRecently` | boolean | Yes | Yes / No, "in the last 12 months" | All roles |
| Physical date | `parq.medicalHistory.physicalDate` | string | Not shown in deck | `MM-DD-YYYY`. Set in 3,037 of the 3,133 documents where Physical is Yes (Open question 5) | All roles |
| Other Conditions | `parq.medicalHistory.physical` | string[] | No | Multi: None, Other, Anxiety, Autism, Depression, Down Syndrome, OCD, Seizures, Stroke, Traumatic Brain Injury | All roles |
| Other Conditions: other | `parq.medicalHistory.physicalOther` | string | When Other | Free text | All roles |
| Other Medications | `parq.medicalHistory.medications` | string[] | No | Multi: None, Other, Allergy, Anti-Anxiety, Antidepressants, Birth Control, Supplements, Vitamins | All roles |
| Other Medications: other | `parq.medicalHistory.medicationsOther` | string | When Other | Free text | All roles |

### 2. Orthopedic History (parity)

Each body part is a multi-select array plus an `*Other` free-text string. Screen copy:
"Click the other button to enter any problem area(s), including any pain, date of
injury, side of the body, date of surgery, physical therapy required & if there has
been a full recovery." No item is marked required.

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Right Foot / Left Foot | `parq.ortho.rightFoot`, `parq.ortho.leftFoot` (+ `rightFootOther`, `leftFootOther`) | string[] + string | No | None, Other, Broken Toe, Bunions, Flat Feet, Fracture, Mortons Neuroma, Plantar Fasciitis | All roles |
| Right Ankle / Left Ankle | `parq.ortho.rightAnkle`, `parq.ortho.leftAnkle` (+ `*Other`) | string[] + string | No | None, Other, Achilles Tendinitis, Fracture, Osteoarthritis, Sprained | All roles |
| Right Knee / Left Knee | `parq.ortho.rightKnee`, `parq.ortho.leftKnee` (+ `*Other`) | string[] + string | No | None, Other, ACL Injury, Bursitis, CMP / Runner’s Knee, Meniscus Tear, Patellar Tendinitis, Replacement. Variants (data): ACL injury, CMP / Runner's Knee (straight apostrophe) | All roles |
| Right Hip / Left Hip | `parq.ortho.rightHip`, `parq.ortho.leftHip` (+ `*Other`) | string[] + string | No | None, Other, Impingement, Labral Tear, Osteoarthritis, Replacement | All roles |
| Back | `parq.ortho.back` (+ `backOther`) | string[] + string | No | None, Other, Bulging Disc, Herniated Disc, Low Back Pain, Muscle / Ligament Strains, Sciatica, Scoliosis, Spinal Stenosis, Spondylolisthesis | All roles |
| Right Shoulder / Left Shoulder | `parq.ortho.rightShoulder`, `parq.ortho.leftShoulder` (+ `*Other`) | string[] + string | No | None, Other, Arthritis, Decreased ROM, Labral Tear, Replacement, Rotator Cuff, Surgery, Tendonitis, Weakness. Variant (data): Laberal Tear | All roles |
| Neck | `parq.ortho.neck` (+ `neckOther`) | string[] + string | No | None, Other, Arthritis, Bulging Disc, Decreased ROM, Fracture, Herniated Disc, Numbness, Pinched Nerve, Surgery, Tightness, Whiplash | All roles |
| Right Elbow / Left Elbow | `parq.ortho.rightElbow`, `parq.ortho.leftElbow` (+ `*Other`) | string[] + string | No | None, Other, Bursitis, Golfers Elbow, Tennis Elbow | All roles |
| Right Wrist / Left Wrist | `parq.ortho.rightWrist`, `parq.ortho.leftWrist` (+ `*Other`) | string[] + string | No | None, Other, Broken, Carpal Tunnel, Sprained, Tendinitis | All roles |
| Right Hand / Left Hand | `parq.ortho.rightHand`, `parq.ortho.leftHand` (+ `*Other`) | string[] + string | No | None, Other, Broken, Broken Finger, Dupuytren's, Osteoarthritis, Sprained, Trigger Finger | All roles |
| Hernia | `parq.ortho.hernia` (+ `herniaOther`) | string[] + string | No | None, Other, Femoral, Hiatal, Incisional, Inguinal, Umbilical. `herniaOther` is missing from 2,774 documents; write it as `""` | All roles |

### 3. Family History (parity)

Each question asks whether the client's mother, father or siblings had the condition.

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Heart Attack (prior to age 55) | `parq.familyHistory.heartAttack` | boolean | No | Yes / No | All roles |
| Heart Surgery (prior to age 55) | `parq.familyHistory.heartSurgery` | boolean | No | Yes / No | All roles |
| High Cholesterol | `parq.familyHistory.highCholesterol` | boolean | No | Yes / No | All roles |
| Stroke (prior to age 50) | `parq.familyHistory.stroke` | boolean | No | Yes / No | All roles |
| Cancer | `parq.familyHistory.cancer` | boolean | No | Yes / No | All roles |
| Obesity | `parq.familyHistory.obesity` | boolean | No | Yes / No | All roles |

### 4. Lifestyle (parity)

The single-choice questions are stored as one-element arrays. No production document
has more than one value in any of them.

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Breakfast | `parq.lifestyle.breakfast` (+ `breakfastOther`) | string[] + string | No | Multi: None, Other, Breakfast Meat, Cereal / Granola, Coffee / Tea, Eggs / Omlette, Fruit / Smoothie, Juice, Toast / Bagel, Yogurt. Variant (data): Eggs / Omelette | All roles |
| Lunch | `parq.lifestyle.lunch` (+ `lunchOther`) | string[] + string | No | Multi: None, Other, Diet Soda, Fast Food, Leftovers, Salad, Sandwich / Wrap, Soda, Soup | All roles |
| Dinner | `parq.lifestyle.dinner` (+ `dinnerOther`) | string[] + string | No | Multi: None, Other, Diet Soda, Light Meal / Snack, Meat / Protein with Vegetables, Pasta / Rice Dish, Soda, Takeout / Restaurant Food, Vegetarian / Vegan Meal | All roles |
| Water (in OZ) | `parq.lifestyle.waterInOz` | int | No | Whole number. 0 in 1,064 documents (blank or real zero is unknown) | All roles |
| Snacks | `parq.lifestyle.snacks` (+ `snacksOther`) | string[] + string | No | Multi: None, Other, Candy / Sweets, Chips / Crackers, Fruit, Nuts / Seeds, Yogurt | All roles |
| Exercise (times per week) | `parq.lifestyle.exercise` | string[] | No | Single: None, 1 – 2, 3 - 4, 5+. Variant (data): 1 - 2 (hyphen; the screen label uses an en dash) | All roles |
| Exercise Type | `parq.lifestyle.exerciseProgram` (+ `exerciseProgramOther`) | string[] + string | No | Multi: None, Other, Bootcamps, Cardio Training, Mobility, Pilates, Running, Spin / Biking, Sports, Strength Training, Swimming, Walking / Hiking, Yoga | All roles |
| Alcohol (drinks per week) | `parq.lifestyle.alcohol` | string[] | No | Single: None, 1 – 2, 3 - 4, 5+. Variant (data): 1 - 2 | All roles |
| Smoking | `parq.lifestyle.smoker` | string[] | No | Single: None, Former, Lite, Moderate, Heavy | All roles |
| Vaping | `parq.lifestyle.vaper` | string[] | No | Single: None, Former, Lite, Moderate, Heavy | All roles |
| Smoke Years | `parq.lifestyle.smokeYears` | int or null | No | Whole number, "Years" suffix. `null` in 804 documents | All roles |
| Smoke Quit Date | `parq.lifestyle.smokeQuitDate` | string | No | `MM/YYYY` | All roles |
| Stress | `parq.lifestyle.stress` | string[] | No | Single: Low, Moderate, High, Variable | All roles |
| Sleep (hours per night) | `parq.lifestyle.sleepHours` | string[] | No | Single: Less than 6 hours, 6 - 8 hours, More than 8 hours | All roles |
| Sleep (wake rested) | `parq.lifestyle.feelRestedAfterSleep` | boolean | No | Yes / No | All roles |

### 5. Goals / Preferences (parity)

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Goals | `parq.goals.primaryGoals` (+ `primaryGoalsOther`) | string[] + string | No | Multi: None, Other, Athletic Performance, Endurance, Flexibility, General Health, Increase Energy, Live Longer, Lose Fat, Mental Health, Mobility, Muscle Building, Rehab, Self Esteem, Stability, Stress Relief, Weight Loss | All roles |
| Goal Weight | `parq.goals.goalWeight` | int | No | Whole number, lbs. 0 in 2,049 documents | All roles |
| Training Days | `parq.goals.trainDay` | string[] | No | Multi: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday | All roles |
| Training Time Start | `parq.goals.trainStarTime` | string | No | Three pickers: hour, minute, AM/PM. Stored as `07 :00 AM` (with a stray space) or `07:00 AM`. Empty picker stored as `--:-- --` | All roles |
| Training Time End | `parq.goals.trainEndTime` | string | No | Same pickers, stored as `08:00 AM` | All roles |
| Sessions per week | `parq.goals.sessionsPerWeek` | number | No | Missing in 996 documents. 11 documents store `2.3` | All roles |
| (no screen) | `parq.goals.secondaryGoals`, `parq.goals.secondaryGoalsOther`, `parq.goals.idealTrainTime` | string[], string, string | — | Always empty in production. Write `[]`, `""`, `""` for parity | All roles |

### 6. Body Assessment (parity)

Screen copy: "Please collect and enter the following biometrics." The body
measurements are stored as **strings** (Open question 7).

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Age | `bodyAssessment.ageInYears` | int | Read-only | Shown as "32 Years". Matches the age computed from `mindBodyData.BirthDate` on the assessment date in 4,787 of 4,795 documents | All roles |
| Height | `bodyAssessment.height` | string | No | ft/in, stored as `5'10"`. Variants (data): `5'10`, `5'` | All roles |
| Weight | `bodyAssessment.weightInLBS` | string | No | lbs, stored as `190` or `190.4` | All roles |
| Body Age | `bodyAssessment.bodyAge` | string | No | Whole number as a string | All roles |
| Body Fat % | `bodyAssessment.bodyFatPercentage` | string | No | Decimal as a string. Shows a rating badge and gauge | All roles |
| Muscle Mass % | `bodyAssessment.muscleMassPercentage` | string | No | Decimal as a string. Shows a rating badge and gauge | All roles |
| Visceral Fat | `bodyAssessment.visceralFat` | int | No | Shown as `12.0` but stored as an int. Gauge bands 1–9, 10–14, ≥15 | All roles |
| Body Mass Index | `bodyAssessment.bodyMassIndex` | string | No | Decimal as a string. Gauge bands <18.5, 18.5–24.9, 25–29.9, ≥30 | All roles |
| Bicep / Calf / Chest / Thigh / Waist (in) | `bodyAssessment.bicepInInches`, `calfInInches`, `chestInInches`, `thighInInches`, `waistInInches` | number | Not shown in deck | Non-zero in about half of all documents, including recent ones (Open question 8) | All roles |

### 7. Fitness Assessment (parity)

Which exercises and tests appear depends on `assessmentType`. See
`docs/reference/exercise-matrix.md` for the full set by type, in display order.

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Resting Heart Rate | `fitnessAssessment.restingHeartRate` | int | No | Whole number. 0 in 3,172 documents | All roles |
| Posture | `fitnessAssessment.posture` | string[] | No | Multi: None, Arched Lower Back, Bow Legged, Foot Pronation, Forward Head, Knock Kneed, Pigeon Toed, Rounded Shoulders | All roles |
| Band company (top level) | `fitnessAssessment.bandCompany` | string | Not shown in deck | Missing from 2,012 documents (Open question 10) | All roles |
| Exercise: Choose Band Company | `fitnessAssessment.program.<key>.bandCompany` | string | No | Perform Better Handle, Perform Better No Handle, Power System Handle, Power System No Handle. Legacy (data): Perform Better, Power Systems | All roles |
| Exercise: Choose Band Color | `fitnessAssessment.program.<key>.colourName` and `.colourBand` | string, string | No | Name plus hex. Perform Better: Purple (Level 1), Pink (Level 2), Magenta (Level 3), Orange (Level 4), Red (Level 5), Green (Level 6). Power Systems: Orange (Extra Light), Green (Light), Yellow (Light), Red (Medium), Green (Medium), Blue (Heavy), Purple (Extra Heavy), Grey (Ultra Heavy); variant Gray (Ultra Heavy) (data) | All roles |
| Exercise: Score | `fitnessAssessment.program.<key>.score` | string | No | Slider: None, Poor, Fair, Good, Excellent (`None` = not attempted) | All roles |
| Exercise: Observation | `fitnessAssessment.program.<key>.observation` (+ `.other`) | string[] + string | No | Multi, with options per exercise. See the "Fitness exercises" table in `docs/reference/sample-docs/field-inventory.md`. Leading-space variants exist (data): ` Excessive Forward Lean`, ` Poor ROM` | All roles |
| Test: Reps | `fitnessAssessment.test.<key>.reps` | int | No | − / + stepper. Screen copy: "All exercises should be 30 seconds." | All roles |
| Test: Timing | `fitnessAssessment.test.<key>.timing` | string | Not shown in deck | `0`, `15`, `30`, `45` or `60` (Open question 11) | All roles |
| Test: Observation | `fitnessAssessment.test.<key>.observation` (+ `.other`) | string[] + string | No | Multi, with options per test (same inventory table) | All roles |

`<key>` is one of the Mongo keys in `exercise-matrix.md`, for example `squats`,
`sidePlankRL`, `overHeadReach`, `s2sEnduranceJump` or `plankOrShoulderTouch`. In the
deck (Adult), band fields appear on Squat, Shoulder Press, Lateral Kicks and Standing
Row only.

### 8. Adaptive Questionnaire (parity)

Screen copy: "Please complete the following for Adaptive / Self-Direction Clients
only." The section is filled in 124 Adaptive documents and also in 129 Adult, 61
Youth and 12 Senior documents (Open question 12).

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Mental and emotional attributes | `adaptiveReport.formOne.mentalEmotionalAttributes` (+ `…Other`) | string[] + string | No | Multi: None, Other, Aggressive Behavior, Anxiety, Controlling Behavior, Dislikes Change, Focus Difficulty, Hypersensitivity | All roles |
| Behavioral triggers | `adaptiveReport.formOne.behavioralTriggers` (+ `…Other`) | string[] + string | No | Multi: None, Other, Change/Transitions, Information Overload, Instructional Demands, Loud Noise, Overstimulation, Touching. Variant (data): Change and Transitions | All roles |
| How a trainer can deescalate | `adaptiveReport.formOne.challengingBehavior` | string | No | Free text | All roles |
| Movies & Television | `adaptiveReport.formOne.moviesAndTelevision` (+ `…Other`) | string[] + string | No | Multi: None, Other, Adventure, Animated, Comedy, Crime, Drama, Horror, Sports, Super-Hero, Thriller, Western | All roles |
| Music | `adaptiveReport.formOne.music` (+ `musicOther`) | string[] + string | No | Multi: None, Other, Classical, Country, Electronic, Jazz, Pop, Rock | All roles |
| Sports | `adaptiveReport.formOne.sports` (+ `sportsOther`) | string[] + string | No | Multi: None, Other, Auto Racing, Baseball, Basketball, Football, Hockey, Soccer | All roles |
| Hobbies | `adaptiveReport.formOne.hobbies` (+ `hobbiesOther`) | string[] + string | No | Multi: None, Other, Biking, Board Games, Gardening, Handicrafts, Hiking, Reading, Video Games | All roles |
| Video Games | `adaptiveReport.formOne.videoGames` (+ `videoGamesOther`) | string[] + string | No | Multi: None, Other, Action, Adventure, Puzzle, Racing, Role Playing, Shooter, Simulation, Sports | All roles |
| Uses reinforcers when resistant | `adaptiveReport.formOne.utilizeReinforcers` | boolean | No | Yes / No | All roles |
| Non-verbal cues | `adaptiveReport.formOne.nonVerbalCues` | string | No | Free text | All roles |
| (no screen) | `adaptiveReport.formOne.howToImplementReinforcers` | string | — | Not shown in deck; almost always empty (Open question 13) | All roles |
| Client mood during assessment | `adaptiveReport.formTwo.clientMood` (+ `clientMoodOther`) | string[] + string | No | Multi: Other, Anxious, Calm, Cheerful, Fearful, Gloomy, Humorous, Indifferent, Quiet, Tense (no None) | All roles |
| Anxiety-provoking behaviors | `adaptiveReport.formTwo.anxietyProvokingBehavior` (+ `…Other`) | string[] + string | No | Multi: None, Other, Being Timid, Compulsive Behavior, Fidgeting, Repetitive Behavior, Stimming | All roles |
| Outburst behaviors | `adaptiveReport.formTwo.outburstBehavior` (+ `…Other`) | string[] + string | No | Multi: None, Other, Hitting, Noncompliance, Resistance to Instruction, Screaming, Throwing | All roles |
| Communication style | `adaptiveReport.formTwo.communicationStyle` | string[] | No | Multi: Limited Verbal, No Sounds, Non-Verbal, Sign Language, Speech Device, Through Caregiver, Verbal (no Other text field) | All roles |
| Caregiver required during sessions | `adaptiveReport.formTwo.isCareGiverRequired` | boolean | No | Yes / No | All roles |
| Communicates independently or through caregiver | `adaptiveReport.formTwo.clientCommunicationMode` | string | No | Single: Independently, Through Caregiver, Both. 46 documents hold run-together values such as `IndependentlyBoth` (Open question 14) | All roles |
| Caregiver involvement | `adaptiveReport.formTwo.careGiverInvolvement` (+ `…Other`) | string[] + string | No | Multi: None, Other, Communication, Encouragement, Required Participation, Required Presence. Variant (data): ` Required Participation` (leading space) | All roles |
| (no screen) | `adaptiveReport.formTwo.careGiverName`, `adaptiveReport.formTwo.careGiverEmergencyContact` | string, string | — | Not shown in deck; filled in a few documents. Contact details (Open question 13) | All roles |

### 9. Complete Assessment (parity)

Every question on this screen is marked required. The mapping of the text prompts is
inferred from stored content, using keyword counts only: workplace words appear in
1,989 `PromptOne` answers, personality words in 477 `PromptTwo` answers, and
semi-private and package words in 565 `PromptThree` answers. Open question 15 asks to
confirm it.

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| Describe the area(s) where your workouts will take place. Include any equipment available. Are there pets? | `finishAssessmentPromptOne` | string | Yes | Free text | All roles |
| Summarize the client for the trainer: personality, how they tolerated the fitness assessment, goals, things to look out for, etc. | `finishAssessmentPromptTwo` | string | Yes | Free text | All roles |
| Are there any opportunities for semi-private training or larger packages? | `finishAssessmentPromptThree` | string | Yes | Free text | All roles |
| Based on what client told you about meals, should we pitch nutrition? | `toAssessor` or `toTheAssessor` (unconfirmed) | boolean | Yes | Yes / No | All roles |
| Do you think the client would benefit from stretch sessions? | `toTheAssessor` or `toAssessor` (unconfirmed) | boolean | Yes | Yes / No | All roles |

### Document fields set by the app or server (parity)

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| — | `_id` | ObjectId | Server | New per document | All roles |
| — | `clientPk` | string | Server | `GG{siteId}{mboClientId}` (Build Spec §7). Owned by flow 02 | All roles |
| — | `trainerPk` | string | Server | `GGT…`. Set from the signed-in trainer, never from the app (Build Spec §5) | All roles |
| — | `mboClientId`, `mboSiteId`, `mboTrainerId`, `mboTrainerName` | string | Server | Mindbody references, not keys. `mboSiteId` is a string (2 legacy ints) | All roles |
| Assessment type | `assessmentType` | string | Yes | Adult, Senior, Youth, Adaptive. Chosen before step 1 (Open question 2) | All roles |
| — | `assessmentCount` | int | Server | Count of this client's assessments including this one (Open question 16) | All roles |
| — | `isReassessment` | boolean | Server | `false` for a first assessment. Missing on documents before June 25, 2025 | All roles |
| — | `isParqFilled`, `isBodyAssessmentFilled`, `isFitnessAssessmentFilled`, `isFinalAssessmentFilled` | boolean | App | Set when each section is saved (see Behavior) | All roles |
| — | `isAssessmentSummaryFilled`, `isMindBodyDataFilled`, `isPtAgreementFilled` | boolean | App | Meaning not confirmed (Open question 17) | All roles |
| — | `ptAgreement` | string | App | Always `""` in production | All roles |
| — | `formsFilled` | int | App | Always 0 in production | All roles |
| — | `assestmentHistory` | ObjectId[] | App | Usually `[]`. Its target is unknown (sample-docs README, item 6) | All roles |
| — | `isDataSyncedToSnowflake` | boolean | Server | `false` on write; the sync job sets it | HQ only (Open question 18) |
| — | `appVersion`, `deviceInfo`, `osInfo` | string | App | Free-form device strings | HQ only (Open question 18) |
| — | `createdAt`, `updatedAt` | date | Server | Server time (Build Spec §5) | All roles |
| — | `__v` | int | Server | Mongoose version key, 0 | — |

### New fields (new, source: GYMGUYZ, Build Spec v0.1 §6)

None of these exist in `packages/schema` yet, and all are additive and optional.

| label | Mongo path | type | required | validation | visible to |
| --- | --- | --- | --- | --- | --- |
| — | `schemaVersion` | int | Server | `2` for documents written by the new app | HQ only |
| — | `sourceApp` | string | Server | `gg-team-v2` | HQ only |
| — | `clientRequestId` | string | App | Generated on the device when the assessment starts; makes offline retries idempotent | — |
| — | `bodyAssessment.numeric.*` | number | Derived | Numeric twins of the string body fields, including height in inches (see Derived values) | All roles |

## Behavior

**Starting.** The trainer reaches step 1 from flow 02 with a client and an assessment
type already chosen. The app creates the document with a `clientRequestId` and shows
Medical History. (New, Build Spec §4.)

**Navigation.** Each screen scrolls and has a back arrow (top left) and a fixed
"Save and Next" button. Back keeps entered values. The last screen's button reads
"Save and Submit". (Parity.)

**Section flags.** Production shows these combinations:

| Combination | Documents |
| --- | --- |
| All four flags true | 3,592 |
| PARQ only | 417 |
| PARQ and body | 191 |
| PARQ, body and fitness | 585 |
| Nothing | 91 |

So a partly finished assessment is saved and can be resumed. The flags are set when
Goals / Preferences (`isParqFilled`), Body Assessment (`isBodyAssessmentFilled`),
Fitness Assessment (`isFitnessAssessmentFilled`) and Complete Assessment
(`isFinalAssessmentFilled`) are saved. (Parity. The exact trigger points are
inferred, see Open question 17.)

**Selection rules.** Picking None clears every other option, and picking any other
option clears None. Single-choice questions allow one option and are stored as a
one-element array. Picking Other shows a text box. The Build Spec requires that text
whenever Other is picked; today 96 Goals answers have Other with no text. (Parity,
plus new from Build Spec §6.)

**Fitness by type.** The app shows only the exercises and tests for the chosen
`assessmentType`, in the matrix order (Open question 9).

**Required fields.** The current app blocks "Save and Next" until the starred fields
on that screen are answered. The Build Spec says nothing beyond client, site and type
is required. Open question 4 decides which rule ships.

**Blank values.** Today a blank number is stored as `0` (`restingHeartRate`,
`waterInOz`, `goalWeight`, test `reps`), and a blank Yes / No as `false`. The Build
Spec (§4, §6) says blanks are stored as absent, never `0`. That changes what parity
means for downstream readers (Open question 6).

**Offline.** The assessment is written to on-device storage on every step change, so
closing the app loses nothing. Saves go into a queue and sync when the phone is
online, keyed by `clientRequestId` so a retry never creates a duplicate. No step in
this flow needs a connection. (New, Build Spec §4.)

**Errors.** If a save to the server fails, the step still advances, because the
local copy is the source until sync. A banner shows "Not synced yet" until the queue
clears. If the server rejects a document (for example, a schema failure), the
assessment stays on the device and is flagged for the trainer. The copy for these
messages is still to be written (Open question 19).

**Empty states.** None. Every screen shows all its questions, including when nothing
is answered yet.

## Derived values

None of these are written into the raw fields, except `ageInYears`, which production
already stores (see Open question 7).

| name | inputs | formula | version |
| --- | --- | --- | --- |
| `ageAtAssessment` | `mindBodyData.BirthDate`, `createdAt` | Whole years between birth date and assessment date. Production also stores this in `bodyAssessment.ageInYears` | v1 |
| `heightInches` | `bodyAssessment.height` | Parse `F'I"` (also `F'I` and `F'`) to `F*12 + I`; anything else gives absent | v1 |
| `bodyNumeric` | `weightInLBS`, `bodyAge`, `bodyFatPercentage`, `muscleMassPercentage`, `bodyMassIndex` | Parse each string to a number; `""` or anything that won't parse gives absent | v1 |
| `bmiComputed` | `heightInches`, `weightInLBS` | `703 × weight ÷ heightInches²`, to one decimal. The entered BMI is within 1.0 of this in 2,941 of 3,283 documents | v1 |
| `bmiCategory` | BMI | <18.5, 18.5–24.9, 25–29.9 (Overweight), ≥30 (Obese). Thresholds read off the gauge; the label below 18.5 isn't visible | v1 (Open question 20) |
| `visceralFatCategory` | `visceralFat` | 1–9, 10–14 (High), ≥15. Labels are not all visible | v1 (Open question 20) |
| `bodyFatCategory`, `muscleMassCategory` | percentage, likely sex and age | Gauge bands seen: <8.0, 8.0–19.9, 20.0–24.9, ≥25.0 (Very High) for one client. The source table isn't known | Open question 20 |
| `normalizedOption` | any option label | Trim spaces; map `1 – 2`/`1 - 2`, `Omlette`/`Omelette`, `Grey`/`Gray`, `Laberal`/`Labral`, `Out Of Breath`/`Out of Breath`, `ACL injury`/`ACL Injury` and straight/curly apostrophes to one key. Read-side only; the stored label is unchanged | v1 |

## Open questions

1. (Gregg) The deck starts at Medical History. Which screens come before it today
   (client pick, assessment type, Mindbody data review, PT agreement), and do they
   belong in this flow or in flow 02?
2. (Gregg) Where and when is `assessmentType` chosen, and can it change after the
   fitness step starts? Seven clients have assessments of more than one type.
3. (Gregg) Step order: keep the current app's nine sections, or move to the Build
   Spec's eight steps (Client, Health, Joints, Goals and lifestyle, Body, Tests,
   Movement, Notes)? The spec ranks below this doc, so this doc needs your call.
4. (Gregg) Required fields: the current app requires Heart, Pacemaker, BP, Chest
   Pain, Metabolic, Pulmonary, Dizziness, Cholesterol, Physical and all five
   Complete Assessment answers. The Build Spec says only client, site and type are
   required to save. Which rule ships? Or should "required to save" and "required to
   submit" be different?
5. (Gregg) Due date and physical date are stored but not shown in the deck. Do they
   appear only when Pregnant or Physical is Yes? Is the date picker `MM-DD-YYYY`?
6. (Gregg) Blank numbers and Yes / No: should the new app store absent (Build Spec)
   or keep writing `0` and `false` (parity)? Snowflake models may read `0` today.
   This changes what the AI brief sees.
7. (Gregg) Body measurements are strings in production. Do we keep writing strings
   (required for parity) and add numeric twins under `bodyAssessment.numeric`, as the
   spec says? Should `ageInYears` keep being stored, given the rule that derived
   values aren't written into raw fields?
8. (Gregg) Where do the bicep, calf, chest, thigh and waist measurements appear?
   They aren't in the deck but are filled in about half of all documents.
9. (Gregg) Fitness by type: write only the type's own exercises (older documents)
   or all 23 exercises and 13 tests with defaults (newer documents)? See
   `exercise-matrix.md`, questions 1–4.
10. (Gregg) Which exercises show band fields? What is the top-level
    `fitnessAssessment.bandCompany` for: a default for the whole session?
11. (Gregg) How is a test's `timing` set? The screen says "All exercises should be
    30 seconds", but the stored values include 0, 15, 45 and 60.
12. (Gregg) Should the Adaptive Questionnaire show for every type, as it does today,
    or only for Adaptive? It is filled for 202 non-Adaptive assessments.
13. (Gregg) `howToImplementReinforcers`, `careGiverName` and
    `careGiverEmergencyContact` aren't in the deck. Are they still collected? The
    last two are contact details for someone other than the client.
14. (Gregg) Fix `clientCommunicationMode` to store a single value going forward?
    Legacy run-together values stay as they are.
15. (Gregg) Confirm the prompt mapping: `PromptOne` is workout area, `PromptTwo` is
    the trainer summary and `PromptThree` is semi-private. Which of `toAssessor` and
    `toTheAssessor` is "pitch nutrition", and which is "stretch sessions"?
16. (Gregg) Is `assessmentCount` counted by the server across all of the client's
    documents, including deleted and partial ones?
17. (Gregg) What do `isAssessmentSummaryFilled`, `isMindBodyDataFilled` and
    `isPtAgreementFilled` mean? (`isAssessmentSummaryFilled` is true without
    `isFinalAssessmentFilled` in 488 documents.) When exactly is each section flag
    set?
18. (Gregg) Should trainers see device and sync metadata, or only HQ?
19. (Gregg) Approve the UI copy for the offline banner, a failed sync and the "Other"
    text box being required.
20. (Gregg) What's the source of the rating bands for BMI, visceral fat, body fat
    and muscle mass (for example, the Omron norms or the "Adult Norms Chart")? Do
    they vary by sex and age?
21. (Gregg) The Resourcifi and Simform scope documents aren't in the repo. Please
    add them to `docs/reference/vendor-scopes/` so each field can be cited.

## Acceptance tests

Run each on an iPhone (Hunter) and an Android phone (Heidi), against a dev database.

1. Start a new Adult assessment for a test client. The first screen is "Medical
   History" with the PARQ tag, and the screen order matches the Steps table.
2. On Heart, tap Stent, then None. Only None stays selected. Tap Stent again, and
   None clears.
3. On Back, tap Other. A text box appears. Type a note, Save and Next, then go back.
   The note is still there, and the saved document has `parq.ortho.back` containing
   `Other` and `parq.ortho.backOther` holding the note.
4. Leave Heart blank and tap Save and Next. The app follows the rule chosen in Open
   question 4: it either blocks with a message naming Heart, or moves on.
5. Fill Medical History and Orthopedic History, then force-close the app. Reopen it.
   The assessment resumes on Family History with every earlier answer kept.
6. Turn on airplane mode, finish an assessment through "Save and Submit", then turn
   airplane mode off. Exactly one document appears in the dev database, and the
   "Not synced yet" banner clears.
7. Enter height `5'10"` and weight `190`. The saved document stores `"5'10\""` and
   `"190"` as strings, and the BMI gauge and badge match `bmiCategory` for 27.3.
8. Start a Senior assessment. Fitness Assessment shows exactly the 10 Senior
   exercises and 4 Senior tests from `exercise-matrix.md`, in that order. Repeat for
   Youth (11 + 4) and Adaptive (11 + 4).
9. On a test, tap + three times and − once. Reps shows 2 and saves as
   `fitnessAssessment.test.<key>.reps = 2`.
10. Leave all Complete Assessment answers blank and tap Save and Submit. The app
    follows Open question 4. When submitted, `isFinalAssessmentFilled` is true.
11. Open a finished document in the dev database. It has `parq.medicalHistory.metobolic`,
    `parq.goals.trainStarTime`, `fitnessAssessment.program.squats.colourName` and
    `assestmentHistory`, spelled exactly like that, and it passes `/parity-check`.
12. In the Adaptive Questionnaire, pick Independently, then Both. The saved
    `clientCommunicationMode` follows Open question 14 and is never `IndependentlyBoth`.
13. Pick "Other" in Goals with no text and tap Save and Next. The app asks for the
    text (Build Spec §6).
14. Sign in as a trainer from another site. The assessment from test 6 can't be
    opened or edited (depends on flow 01).

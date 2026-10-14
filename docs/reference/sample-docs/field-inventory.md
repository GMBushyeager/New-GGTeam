# prod.assessments field inventory

Generated from a full export of `prod.assessments` (4,877 documents, created January 6, 2025 through October 14, 2026).
It lists every field path, its stored type, and how many documents have it. Option values with their
counts are listed only for closed-list fields. Free text, names, IDs, contact details and dates are never listed.

`[]` marks array elements. `$oid` and `$date` are MongoDB Extended JSON. Field names are copied exactly from
production, including misspellings.


## Top-level fields

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `__v` | int | 4,877 |  |
| `_id` | $oid | 4,877 |  |
| `appVersion` | str | 4,337 | `2.0.8` (769); `2.0.4` (676); `1.7` (492); `2.0.1` (425); `1.5` (328); `2.0.5` (204); `1.2.0` (197); `2.0.2` (162); `2.0.7` (158); `2.0.6` (143); `1.1.6` (142); `1.0.9` (120); `1.1.3` (112); `1.0.8` (92); `1.9` (69); `1.1.4` (58); `1.1.7` (54); `1.1.9` (36); `1.1.8` (23); `1.1.2` (21); `1.8` (19); `""` (17); `2.0` (10); `2.0.3` (7); `1.0.7` (2); `1.0.6` (1) |
| `assessmentCount` | int | 4,877 |  |
| `assessmentType` | str | 4,875 | `Adult` (3307); `Senior` (672); `Youth` (493); `Adaptive` (403) |
| `assestmentHistory` | array | 3,899 |  |
| `assestmentHistory[]` | $oid | 120 |  |
| `clientPk` | str | 4,877 |  |
| `createdAt` | $date | 4,877 |  |
| `deviceInfo` | str | 4,337 |  |
| `finishAssessmentPromptOne` | str | 4,877 |  |
| `finishAssessmentPromptThree` | str | 4,877 |  |
| `finishAssessmentPromptTwo` | str | 4,877 |  |
| `formsFilled` | int | 4,877 |  |
| `isAssessmentSummaryFilled` | bool | 4,877 | `True` (4080); `False` (797) |
| `isBodyAssessmentFilled` | bool | 4,877 | `True` (4368); `False` (509) |
| `isDataSyncedToSnowflake` | bool | 4,877 | `True` (3759); `False` (1118) |
| `isFinalAssessmentFilled` | bool | 4,877 | `True` (3593); `False` (1284) |
| `isFitnessAssessmentFilled` | bool | 4,877 | `True` (4177); `False` (700) |
| `isMindBodyDataFilled` | bool | 4,877 | `True` (4874); `False` (3) |
| `isParqFilled` | bool | 4,877 | `True` (4786); `False` (91) |
| `isPtAgreementFilled` | bool | 4,877 | `True` (4740); `False` (137) |
| `isReassessment` | bool | 3,908 | `False` (3016); `True` (892) |
| `mboClientId` | str | 4,877 |  |
| `mboSiteId` | str (4875), int (2) | 4,877 |  |
| `mboTrainerId` | str | 4,877 |  |
| `mboTrainerName` | str | 4,877 |  |
| `osInfo` | str | 4,337 |  |
| `ptAgreement` | str | 4,877 |  |
| `toAssessor` | bool | 4,877 | `False` (3831); `True` (1046) |
| `toTheAssessor` | bool | 4,877 | `False` (3728); `True` (1149) |
| `trainerPk` | str | 4,877 |  |
| `updatedAt` | $date | 4,877 |  |

## `adaptiveReport`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `adaptiveReport` | object | 4,877 |  |
| `adaptiveReport.formOne` | object | 4,877 |  |
| `adaptiveReport.formOne.behavioralTriggers` | array | 4,877 |  |
| `adaptiveReport.formOne.behavioralTriggersOther` | str | 4,877 |  |
| `adaptiveReport.formOne.behavioralTriggers[]` | str | 317 | `None` (179); `Information Overload` (69); `Overstimulation` (63); `Change/Transitions` (57); `Instructional Demands` (42); `Loud Noise` (27); `Touching` (21); `Other` (18); `Change and Transitions` (1) |
| `adaptiveReport.formOne.challengingBehavior` | str | 4,877 |  |
| `adaptiveReport.formOne.hobbies` | array | 4,877 |  |
| `adaptiveReport.formOne.hobbiesOther` | str | 4,877 |  |
| `adaptiveReport.formOne.hobbies[]` | str | 287 | `None` (110); `Other` (104); `Video Games` (46); `Reading` (26); `Hiking` (21); `Handicrafts` (17); `Biking` (17); `Board Games` (14); `Gardening` (8) |
| `adaptiveReport.formOne.howToImplementReinforcers` | str | 4,877 |  |
| `adaptiveReport.formOne.mentalEmotionalAttributes` | array | 4,877 |  |
| `adaptiveReport.formOne.mentalEmotionalAttributesOther` | str | 4,877 |  |
| `adaptiveReport.formOne.mentalEmotionalAttributes[]` | str | 339 | `None` (156); `Anxiety` (94); `Focus Difficulty` (88); `Dislikes Change` (47); `Other` (43); `Hypersensitivity` (31); `Aggressive Behavior` (29); `Controlling Behavior` (22) |
| `adaptiveReport.formOne.moviesAndTelevision` | array | 4,877 |  |
| `adaptiveReport.formOne.moviesAndTelevisionOther` | str | 4,877 |  |
| `adaptiveReport.formOne.moviesAndTelevision[]` | str | 290 | `None` (139); `Other` (62); `Animated` (58); `Adventure` (41); `Comedy` (34); `Super-Hero` (22); `Drama` (20); `Crime` (19); `Horror` (17); `Sports` (14); `Thriller` (14); `Western` (4) |
| `adaptiveReport.formOne.music` | array | 4,877 |  |
| `adaptiveReport.formOne.musicOther` | str | 4,877 |  |
| `adaptiveReport.formOne.music[]` | str | 284 | `None` (120); `Other` (80); `Pop` (72); `Rock` (39); `Classical` (32); `Country` (32); `Jazz` (21); `Electronic` (18) |
| `adaptiveReport.formOne.nonVerbalCues` | str | 4,877 |  |
| `adaptiveReport.formOne.sports` | array | 4,877 |  |
| `adaptiveReport.formOne.sportsOther` | str | 4,877 |  |
| `adaptiveReport.formOne.sports[]` | str | 289 | `None` (164); `Other` (50); `Basketball` (40); `Football` (34); `Baseball` (27); `Soccer` (16); `Hockey` (16); `Auto Racing` (14) |
| `adaptiveReport.formOne.utilizeReinforcers` | bool | 4,877 | `False` (4843); `True` (34) |
| `adaptiveReport.formOne.videoGames` | array | 4,877 |  |
| `adaptiveReport.formOne.videoGamesOther` | str | 4,877 |  |
| `adaptiveReport.formOne.videoGames[]` | str | 273 | `None` (185); `Other` (32); `Action` (32); `Adventure` (24); `Role Playing` (20); `Shooter` (17); `Simulation` (15); `Racing` (13); `Puzzle` (11); `Sports` (10) |
| `adaptiveReport.formTwo` | object | 4,877 |  |
| `adaptiveReport.formTwo.anxietyProvokingBehavior` | array | 4,877 |  |
| `adaptiveReport.formTwo.anxietyProvokingBehaviorOther` | str | 4,877 |  |
| `adaptiveReport.formTwo.anxietyProvokingBehavior[]` | str | 300 | `None` (191); `Being Timid` (50); `Fidgeting` (48); `Stimming` (28); `Compulsive Behavior` (26); `Repetitive Behavior` (24); `Other` (13) |
| `adaptiveReport.formTwo.careGiverEmergencyContact` | str | 4,877 |  |
| `adaptiveReport.formTwo.careGiverInvolvement` | array | 4,877 |  |
| `adaptiveReport.formTwo.careGiverInvolvementOther` | str | 4,877 |  |
| `adaptiveReport.formTwo.careGiverInvolvement[]` | str | 288 | `Encouragement` (139); `Communication` (110); `None` (94); `Required Presence` (61); ` Required Participation` (32); `Other` (18); `Required Participation` (7) |
| `adaptiveReport.formTwo.careGiverName` | str | 4,877 |  |
| `adaptiveReport.formTwo.clientCommunicationMode` | str | 4,877 |  |
| `adaptiveReport.formTwo.clientMood` | array | 4,877 |  |
| `adaptiveReport.formTwo.clientMoodOther` | str | 4,877 |  |
| `adaptiveReport.formTwo.clientMood[]` | str | 304 | `Calm` (171); `Cheerful` (120); `Anxious` (65); `Humorous` (62); `Quiet` (52); `Indifferent` (43); `Tense` (23); `Other` (21); `Fearful` (10); `Gloomy` (7) |
| `adaptiveReport.formTwo.communicationStyle` | array | 4,877 |  |
| `adaptiveReport.formTwo.communicationStyle[]` | str | 280 | `Verbal` (179); `Limited Verbal` (65); `Non-Verbal` (38); `Through Caregiver` (33); `No Sounds` (15); `Speech Device` (13); `Sign Language` (12) |
| `adaptiveReport.formTwo.isCareGiverRequired` | bool | 4,877 | `False` (4812); `True` (65) |
| `adaptiveReport.formTwo.outburstBehavior` | array | 4,877 |  |
| `adaptiveReport.formTwo.outburstBehaviorOther` | str | 4,877 |  |
| `adaptiveReport.formTwo.outburstBehavior[]` | str | 296 | `None` (233); `Resistance to Instruction` (38); `Noncompliance` (26); `Screaming` (17); `Hitting` (15); `Other` (10); `Throwing` (10) |

## `bodyAssessment`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `bodyAssessment` | object | 4,877 |  |
| `bodyAssessment.ageInYears` | int | 4,877 |  |
| `bodyAssessment.bicepInInches` | int (4272), float (605) | 4,877 |  |
| `bodyAssessment.bodyAge` | str | 4,877 |  |
| `bodyAssessment.bodyFatPercentage` | str | 4,877 |  |
| `bodyAssessment.bodyMassIndex` | str | 4,877 |  |
| `bodyAssessment.calfInInches` | int (4302), float (575) | 4,877 |  |
| `bodyAssessment.chestInInches` | int (4407), float (470) | 4,877 |  |
| `bodyAssessment.height` | str | 4,877 |  |
| `bodyAssessment.muscleMassPercentage` | str | 4,877 |  |
| `bodyAssessment.thighInInches` | int (4350), float (527) | 4,877 |  |
| `bodyAssessment.visceralFat` | int | 4,877 |  |
| `bodyAssessment.waistInInches` | int (4381), float (496) | 4,877 |  |
| `bodyAssessment.weightInLBS` | str | 4,877 |  |

## `comments`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `comments` | object | 3,881 |  |
| `comments.bodyAssessmentComment` | str | 3,877 |  |
| `comments.finalAssessmentComment` | str | 3,876 |  |
| `comments.fitnessAssessmentComment` | str | 3,878 |  |
| `comments.mindBodyDataComment` | str | 3,878 |  |
| `comments.parqComment` | str | 3,876 |  |

## `fitnessAssessment`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `fitnessAssessment` | object | 4,877 |  |
| `fitnessAssessment.bandCompany` | str | 2,865 | `""` (712); `Perform Better Handle` (701); `Power System Handle` (620); `Power Systems` (315); `Perform Better` (263); `Perform Better No Handle` (169); `Power System No Handle` (85) |
| `fitnessAssessment.posture` | array | 4,877 |  |
| `fitnessAssessment.posture[]` | str | 2,980 | `None` (1342); `Rounded Shoulders` (1068); `Forward Head` (733); `Arched Lower Back` (469); `Foot Pronation` (305); `Knock Kneed` (184); `Pigeon Toed` (147); `Bow Legged` (142) |
| `fitnessAssessment.program` | object | 4,012 |  |
| `fitnessAssessment.program.<exercise>` | object | 3,881 |  |
| `fitnessAssessment.program.<exercise>.bandCompany` | str | 2,086 | `""` (1724); `Power Systems` (144); `Perform Better Handle` (102); `Perform Better` (97); `Power System Handle` (19) |
| `fitnessAssessment.program.<exercise>.colourBand` | str | 3,881 |  |
| `fitnessAssessment.program.<exercise>.colourName` | str | 3,881 | `""` (3244); `Purple (Level 1)` (177); `Red (Medium)` (95); `Orange (Extra Light)` (94); `Green (Light)` (87); `Magenta (Level 3)` (31); `Orange (Level 4)` (29); `Pink (Level 2)` (26); `Red (Level 5)` (26); `Blue (Heavy)` (25); `Green (Level 6)` (18); `Green (Medium)` (11); `Purple (Extra Heavy)` (7); `Yellow (Light)` (6); `Grey (Ultra Heavy)` (4); `Gray (Ultra Heavy)` (1) |
| `fitnessAssessment.program.<exercise>.observation` | array | 3,881 |  |
| `fitnessAssessment.program.<exercise>.observation[]` | str | 2,250 | `Coachable` (894); `Other` (690); ` Excessive Forward Lean` (579); `None` (359); `Poor ROM` (352); `Heels Raised` (337); `Great ROM` (288); `Pronated Feet` (182); `Rounding` (172); `Valgus` (131); `Arching` (96) |
| `fitnessAssessment.program.<exercise>.other` | str | 3,463 |  |
| `fitnessAssessment.program.<exercise>.score` | str | 3,881 | `Good` (831); `None` (824); `""` (815); `Fair` (760); `Excellent` (396); `Poor` (255) |
| `fitnessAssessment.restingHeartRate` | int | 4,877 |  |
| `fitnessAssessment.test` | object | 4,877 |  |
| `fitnessAssessment.test.<test>` | object | 4,694 |  |
| `fitnessAssessment.test.<test>.observation` | array | 3,596 |  |
| `fitnessAssessment.test.<test>.observation[]` | str | 2,221 | `On Knees` (714); `Other` (661); `1 / 2 ROM` (622); `Full ROM` (336); `None` (312); `Dropped Hips` (196); `Shrugging` (188); `1 / 4 ROM` (175); `Neck Movement` (156) |
| `fitnessAssessment.test.<test>.other` | str | 2,723 |  |
| `fitnessAssessment.test.<test>.reps` | int | 4,694 |  |
| `fitnessAssessment.test.<test>.timing` | str | 4,304 | `30` (1673); `""` (1188); `0` (946); `15` (408); `45` (53); `60` (36) |

## `mindBodyData`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `mindBodyData` | object | 4,877 |  |
| `mindBodyData.AddressLine1` | str | 4,877 |  |
| `mindBodyData.BirthDate` | str | 4,874 |  |
| `mindBodyData.City` | str | 4,877 |  |
| `mindBodyData.Country` | str | 4,377 |  |
| `mindBodyData.Email` | str | 4,877 |  |
| `mindBodyData.EmergencyContactInfoName` | str | 4,877 |  |
| `mindBodyData.EmergencyContactInfoPhone` | str | 4,877 |  |
| `mindBodyData.EmergencyContactInfoRelationship` | str | 4,877 |  |
| `mindBodyData.FirstName` | str | 4,877 |  |
| `mindBodyData.Gender` | str | 4,877 |  |
| `mindBodyData.LastName` | str | 4,877 |  |
| `mindBodyData.MobilePhone` | str | 4,877 |  |
| `mindBodyData.PostalCode` | str | 4,877 |  |
| `mindBodyData.ReferredBy` | str | 4,877 |  |
| `mindBodyData.SendAccountEmails` | bool | 4,877 |  |
| `mindBodyData.SendPromotionalEmails` | bool | 4,877 |  |
| `mindBodyData.SendScheduleEmails` | bool | 4,877 |  |
| `mindBodyData.State` | str | 4,794 |  |
| `mindBodyData.clientType` | str | 4,377 |  |

## `parq`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `parq` | object | 4,877 |  |
| `parq.familyHistory` | object | 4,877 |  |
| `parq.familyHistory.cancer` | bool | 4,877 | `False` (3641); `True` (1236) |
| `parq.familyHistory.heartAttack` | bool | 4,877 | `False` (4253); `True` (624) |
| `parq.familyHistory.heartSurgery` | bool | 4,877 | `False` (4429); `True` (448) |
| `parq.familyHistory.highCholesterol` | bool | 4,877 | `False` (3088); `True` (1789) |
| `parq.familyHistory.obesity` | bool | 4,877 | `False` (3466); `True` (1411) |
| `parq.familyHistory.stroke` | bool | 4,877 | `False` (4503); `True` (374) |
| `parq.goals` | object | 4,877 |  |
| `parq.goals.goalWeight` | int | 4,877 |  |
| `parq.goals.idealTrainTime` | str | 4,162 |  |
| `parq.goals.primaryGoals` | array | 4,877 |  |
| `parq.goals.primaryGoalsOther` | str | 4,877 |  |
| `parq.goals.primaryGoals[]` | str | 4,420 | `Muscle Building` (2656); `General Health` (2282); `Weight Loss` (1909); `Lose Fat` (1792); `Other` (1519); `Mobility` (1402); `Increase Energy` (1312); `Flexibility` (1188); `Live Longer` (1060); `Endurance` (923); `Stability` (874); `Stress Relief` (849); `Mental Health` (757); `Athletic Performance` (702); `Self Esteem` (551); `Rehab` (224); `None` (80) |
| `parq.goals.secondaryGoals` | array | 4,162 |  |
| `parq.goals.secondaryGoalsOther` | str | 4,162 |  |
| `parq.goals.sessionsPerWeek` | int (3844), float (37) | 3,881 |  |
| `parq.goals.trainDay` | array | 4,877 |  |
| `parq.goals.trainDay[]` | str | 4,017 | `Monday` (2555); `Wednesday` (2364); `Thursday` (2356); `Friday` (2353); `Tuesday` (2321); `Saturday` (1295); `Sunday` (777) |
| `parq.goals.trainEndTime` | str | 4,877 |  |
| `parq.goals.trainStarTime` | str | 4,877 |  |
| `parq.lifestyle` | object | 4,877 |  |
| `parq.lifestyle.alcohol` | array | 4,877 |  |
| `parq.lifestyle.alcohol[]` | str | 4,303 | `None` (2467); `1 – 2` (778); `5+` (439); `3 - 4` (386); `1 - 2` (233) |
| `parq.lifestyle.breakfast` | array | 4,877 |  |
| `parq.lifestyle.breakfastOther` | str | 4,877 |  |
| `parq.lifestyle.breakfast[]` | str | 4,383 | `Other` (1891); `Coffee / Tea` (1451); `Eggs / Omlette` (1145); `Fruit / Smoothie` (923); `Toast / Bagel` (808); `Cereal / Granola` (786); `Yogurt` (643); `None` (496); `Breakfast Meat` (385); `Eggs / Omelette` (298); `Juice` (126) |
| `parq.lifestyle.dinner` | array | 4,877 |  |
| `parq.lifestyle.dinnerOther` | str | 4,877 |  |
| `parq.lifestyle.dinner[]` | str | 4,346 | `Meat / Protein with Vegetables` (2589); `Other` (1769); `Pasta / Rice Dish` (1404); `Takeout / Restaurant Food` (810); `Vegetarian / Vegan Meal` (470); `Light Meal / Snack` (268); `None` (204); `Diet Soda` (141); `Soda` (102) |
| `parq.lifestyle.exercise` | array | 4,877 |  |
| `parq.lifestyle.exerciseProgram` | array | 4,877 |  |
| `parq.lifestyle.exerciseProgramOther` | str | 4,877 |  |
| `parq.lifestyle.exerciseProgram[]` | str | 4,249 | `Walking / Hiking` (1413); `Other` (1169); `None` (1160); `Strength Training` (992); `Cardio Training` (700); `Sports` (309); `Spin / Biking` (301); `Mobility` (253); `Running` (252); `Yoga` (224); `Pilates` (176); `Bootcamps` (147); `Swimming` (113) |
| `parq.lifestyle.exercise[]` | str | 4,274 | `None` (1734); `3 - 4` (915); `1 – 2` (759); `5+` (689); `1 - 2` (177) |
| `parq.lifestyle.feelRestedAfterSleep` | bool | 4,877 | `True` (2621); `False` (2256) |
| `parq.lifestyle.lunch` | array | 4,877 |  |
| `parq.lifestyle.lunchOther` | str | 4,877 |  |
| `parq.lifestyle.lunch[]` | str | 4,341 | `Other` (2307); `Sandwich / Wrap` (1485); `Salad` (1050); `Leftovers` (724); `Fast Food` (416); `None` (405); `Soup` (233); `Diet Soda` (197); `Soda` (130) |
| `parq.lifestyle.sleepHours` | array | 4,877 |  |
| `parq.lifestyle.sleepHours[]` | str | 4,291 | `6 - 8 hours` (2647); `Less than 6 hours` (970); `More than 8 hours` (674) |
| `parq.lifestyle.smokeQuitDate` | str | 4,877 |  |
| `parq.lifestyle.smokeYears` | int (4073), null (804) | 4,877 |  |
| `parq.lifestyle.smoker` | array | 4,877 |  |
| `parq.lifestyle.smoker[]` | str | 4,276 | `None` (3791); `Former` (315); `Lite` (92); `Moderate` (52); `Heavy` (26) |
| `parq.lifestyle.snacks` | array | 4,877 |  |
| `parq.lifestyle.snacksOther` | str | 4,877 |  |
| `parq.lifestyle.snacks[]` | str | 4,270 | `Other` (1556); `Chips / Crackers` (1376); `Fruit` (1113); `Candy / Sweets` (1025); `Nuts / Seeds` (966); `None` (853); `Yogurt` (448) |
| `parq.lifestyle.stress` | array | 4,877 |  |
| `parq.lifestyle.stress[]` | str | 4,257 | `Moderate` (1413); `Low` (1230); `High` (1037); `Variable` (577) |
| `parq.lifestyle.vaper` | array | 4,877 |  |
| `parq.lifestyle.vaper[]` | str | 4,187 | `None` (3996); `Lite` (74); `Former` (45); `Moderate` (44); `Heavy` (28) |
| `parq.lifestyle.waterInOz` | int | 4,877 |  |
| `parq.medicalHistory` | object | 4,877 |  |
| `parq.medicalHistory.bp` | array | 4,877 |  |
| `parq.medicalHistory.bpOther` | str | 4,877 |  |
| `parq.medicalHistory.bp[]` | str | 4,786 | `None` (3591); `Other` (660); `Hypertension` (432); `Statin (med)` (167); `Beta Blocker (med)` (98); `Angioplasty` (88); `ACE Inhibitor(med)` (70); `Aspirin (med)` (46); `Anticoagulant (med)` (44); `Diuretics (med)` (39); `Calcium Blocker (med)` (23) |
| `parq.medicalHistory.chestPain` | array | 4,877 |  |
| `parq.medicalHistory.chestPainOther` | str | 4,877 |  |
| `parq.medicalHistory.chestPain[]` | str | 4,786 | `None` (4424); `Other` (203); `Reflux` (81); `Gastritis` (64); `Angina` (60); `Rib Fracture` (37); `Pericarditis` (28) |
| `parq.medicalHistory.cholesterol` | array | 4,877 |  |
| `parq.medicalHistory.cholesterolOther` | str | 4,877 |  |
| `parq.medicalHistory.cholesterol[]` | str | 4,786 | `None` (3510); `Other` (580); `High LDL` (401); `Statins (med)` (293); `High Triglycerides` (160); `Angina` (66); `Hypercholesterolemia` (59); `Atherosclerosis` (54); `Cholesterol Absorption Inhibitors (med)` (50); `CoQ10 (med)` (37); `ACL Inhibitors (med)` (28); `PCSK9 Inhibitors (med)` (5) |
| `parq.medicalHistory.dizziness` | array | 4,877 |  |
| `parq.medicalHistory.dizzinessOther` | str | 4,877 |  |
| `parq.medicalHistory.dizziness[]` | str | 4,786 | `None` (3895); `Other` (513); `Dizziness` (405); `Vertigo` (157); `Unexplained Shortness of Breath` (136); `Fainting` (125) |
| `parq.medicalHistory.dueDate` | str | 4,877 |  |
| `parq.medicalHistory.havePhysicalRecently` | bool | 4,877 | `True` (3133); `False` (1744) |
| `parq.medicalHistory.heart` | array | 4,877 |  |
| `parq.medicalHistory.heartOther` | str | 4,877 |  |
| `parq.medicalHistory.heart[]` | str | 4,786 | `None` (3997); `Other` (537); `Cardiovascular Disease` (81); `Stent` (80); `Arteriosclerosis` (69); `Congestive Heart Failure` (69); `Statin (med)` (69); `Heart Attack` (63); `Beta Blocker (med)` (54); `Bypass` (52); `Coronary Heart Disease` (51); `Stroke` (48); `Aspirin (med)` (46); `Diuretics (med)` (39); `Surgery` (33); `Anticoagulant (med)` (26); `ACE Inhibitor (med)` (21) |
| `parq.medicalHistory.lastBp` | str | 4,877 |  |
| `parq.medicalHistory.medications` | array | 4,877 |  |
| `parq.medicalHistory.medicationsOther` | str | 4,877 |  |
| `parq.medicalHistory.medications[]` | str | 4,501 | `None` (1927); `Other` (1547); `Vitamins` (1119); `Supplements` (720); `Anti-Anxiety` (350); `Allergy` (260); `Antidepressants` (227); `Birth Control` (90) |
| `parq.medicalHistory.metobolic` | array | 4,877 |  |
| `parq.medicalHistory.metobolicOther` | str | 4,877 |  |
| `parq.medicalHistory.metobolic[]` | str | 4,786 | `None` (3703); `Other` (429); `Type II Diabetes` (235); `Prediabetes` (184); `Thyroid` (160); `Hypothyroidism (med)` (145); `Fatty Liver` (103); `Type I Diabetes` (83); `Kidney` (59); `Hashimotos` (57); `Hyperthyroidism (med)` (45); `Insulin (med)` (43); `Graves` (40); `Statin (med)` (37); `Anti-Diabetic (med)` (25); `Keto` (22); `Renal` (13); `Anti-diabetic (med)` (11) |
| `parq.medicalHistory.other` | str | 1,250 |  |
| `parq.medicalHistory.overweight` | bool | 4,877 | `False` (2696); `True` (2181) |
| `parq.medicalHistory.paceMaker` | array | 4,877 |  |
| `parq.medicalHistory.paceMakerOther` | str | 4,877 |  |
| `parq.medicalHistory.paceMaker[]` | str | 4,786 | `None` (4563); `Implantable Defibrillator` (114); `Pacemaker` (89); `Other` (77) |
| `parq.medicalHistory.physical` | array | 4,877 |  |
| `parq.medicalHistory.physicalDate` | str | 4,877 |  |
| `parq.medicalHistory.physicalOther` | str | 4,877 |  |
| `parq.medicalHistory.physical[]` | str | 4,525 | `None` (2979); `Anxiety` (731); `Other` (660); `Depression` (423); `Autism` (249); `OCD` (102); `Stroke` (79); `Down Syndrome` (75); `Seizures` (62); `Traumatic Brain Injury` (57) |
| `parq.medicalHistory.pregnant` | bool | 4,877 | `False` (4842); `True` (35) |
| `parq.medicalHistory.pulmonary` | array | 4,877 |  |
| `parq.medicalHistory.pulmonaryOther` | str | 4,877 |  |
| `parq.medicalHistory.pulmonary[]` | str | 4,786 | `None` (3940); `Other` (470); `Exercise Induced Asthma` (235); `Rescue Inhaler (med)` (157); `Maintenance Inhaler (med)` (144); `Persistent Asthma` (132); `COPD` (100) |
| `parq.ortho` | object | 4,877 |  |
| `parq.ortho.back` | array | 4,877 |  |
| `parq.ortho.backOther` | str | 4,877 |  |
| `parq.ortho.back[]` | str | 4,395 | `None` (2632); `Other` (1025); `Low Back Pain` (771); `Sciatica` (196); `Herniated Disc` (187); `Scoliosis` (138); `Bulging Disc` (120); `Muscle / Ligament Strains` (69); `Spinal Stenosis` (66); `Spondylolisthesis` (17) |
| `parq.ortho.hernia` | array | 4,877 |  |
| `parq.ortho.herniaOther` | str | 2,103 |  |
| `parq.ortho.hernia[]` | str | 4,285 | `None` (3813); `Other` (290); `Umbilical` (115); `Inguinal` (91); `Hiatal` (63); `Incisional` (37); `Femoral` (27) |
| `parq.ortho.leftAnkle` | array | 4,877 |  |
| `parq.ortho.leftAnkleOther` | str | 4,877 |  |
| `parq.ortho.leftAnkle[]` | str | 4,344 | `None` (3732); `Other` (391); `Sprained` (157); `Achilles Tendinitis` (99); `Fracture` (88); `Osteoarthritis` (40) |
| `parq.ortho.leftElbow` | array | 4,877 |  |
| `parq.ortho.leftElbowOther` | str | 4,877 |  |
| `parq.ortho.leftElbow[]` | str | 4,304 | `None` (4065); `Other` (146); `Tennis Elbow` (66); `Golfers Elbow` (36); `Bursitis` (30) |
| `parq.ortho.leftFoot` | array | 4,877 |  |
| `parq.ortho.leftFootOther` | str | 4,877 |  |
| `parq.ortho.leftFoot[]` | str | 4,391 | `None` (3557); `Other` (526); `Plantar Fasciitis` (156); `Flat Feet` (142); `Broken Toe` (93); `Bunions` (90); `Fracture` (48); `Mortons Neuroma` (34) |
| `parq.ortho.leftHand` | array | 4,877 |  |
| `parq.ortho.leftHandOther` | str | 4,877 |  |
| `parq.ortho.leftHand[]` | str | 4,300 | `None` (3856); `Other` (287); `Osteoarthritis` (105); `Broken Finger` (52); `Broken` (33); `Dupuytren's` (24); `Trigger Finger` (19); `Sprained` (9) |
| `parq.ortho.leftHip` | array | 4,877 |  |
| `parq.ortho.leftHipOther` | str | 4,877 |  |
| `parq.ortho.leftHip[]` | str | 4,344 | `None` (3725); `Other` (454); `Impingement` (83); `Osteoarthritis` (70); `Replacement` (62); `Labral Tear` (28) |
| `parq.ortho.leftKnee` | array | 4,877 |  |
| `parq.ortho.leftKneeOther` | str | 4,877 |  |
| `parq.ortho.leftKnee[]` | str | 4,379 | `None` (3333); `Other` (814); `Meniscus Tear` (102); `Replacement` (93); `Patellar Tendinitis` (53); `ACL injury` (46); `CMP / Runner’s Knee` (45); `Bursitis` (42); `ACL Injury` (24); `CMP / Runner's Knee` (23) |
| `parq.ortho.leftShoulder` | array | 4,877 |  |
| `parq.ortho.leftShoulderOther` | str | 4,877 |  |
| `parq.ortho.leftShoulder[]` | str | 4,337 | `None` (3543); `Other` (493); `Rotator Cuff` (132); `Weakness` (129); `Decreased ROM` (114); `Arthritis` (80); `Tendonitis` (58); `Laberal Tear` (30); `Surgery` (25); `Replacement` (23); `Labral Tear` (18) |
| `parq.ortho.leftWrist` | array | 4,877 |  |
| `parq.ortho.leftWristOther` | str | 4,877 |  |
| `parq.ortho.leftWrist[]` | str | 4,299 | `None` (3848); `Other` (310); `Broken` (88); `Carpal Tunnel` (79); `Tendinitis` (49); `Sprained` (39) |
| `parq.ortho.neck` | array | 4,877 |  |
| `parq.ortho.neckOther` | str | 4,877 |  |
| `parq.ortho.neck[]` | str | 4,330 | `None` (3386); `Other` (501); `Tightness` (379); `Arthritis` (86); `Pinched Nerve` (84); `Decreased ROM` (73); `Herniated Disc` (65); `Bulging Disc` (50); `Whiplash` (37); `Surgery` (34); `Numbness` (25); `Fracture` (13) |
| `parq.ortho.rightAnkle` | array | 4,877 |  |
| `parq.ortho.rightAnkleOther` | str | 4,877 |  |
| `parq.ortho.rightAnkle[]` | str | 4,335 | `None` (3703); `Other` (431); `Sprained` (159); `Achilles Tendinitis` (96); `Fracture` (82); `Osteoarthritis` (43) |
| `parq.ortho.rightElbow` | array | 4,877 |  |
| `parq.ortho.rightElbowOther` | str | 4,877 |  |
| `parq.ortho.rightElbow[]` | str | 4,281 | `None` (3990); `Other` (193); `Tennis Elbow` (80); `Bursitis` (36); `Golfers Elbow` (30) |
| `parq.ortho.rightFoot` | array | 4,877 |  |
| `parq.ortho.rightFootOther` | str | 4,877 |  |
| `parq.ortho.rightFoot[]` | str | 4,389 | `None` (3504); `Other` (564); `Plantar Fasciitis` (163); `Flat Feet` (133); `Broken Toe` (93); `Bunions` (87); `Fracture` (62); `Mortons Neuroma` (46) |
| `parq.ortho.rightHand` | array | 4,877 |  |
| `parq.ortho.rightHandOther` | str | 4,877 |  |
| `parq.ortho.rightHand[]` | str | 4,302 | `None` (3825); `Other` (299); `Osteoarthritis` (111); `Broken Finger` (44); `Broken` (34); `Trigger Finger` (33); `Sprained` (23); `Dupuytren's` (17) |
| `parq.ortho.rightHip` | array | 4,877 |  |
| `parq.ortho.rightHipOther` | str | 4,877 |  |
| `parq.ortho.rightHip[]` | str | 4,341 | `None` (3643); `Other` (523); `Impingement` (93); `Replacement` (90); `Osteoarthritis` (58); `Labral Tear` (39) |
| `parq.ortho.rightKnee` | array | 4,877 |  |
| `parq.ortho.rightKneeOther` | str | 4,877 |  |
| `parq.ortho.rightKnee[]` | str | 4,367 | `None` (3185); `Other` (892); `Meniscus Tear` (130); `ACL Injury` (97); `Replacement` (88); `CMP / Runner’s Knee` (64); `Patellar Tendinitis` (57); `Bursitis` (37); `CMP / Runner's Knee` (23) |
| `parq.ortho.rightShoulder` | array | 4,877 |  |
| `parq.ortho.rightShoulderOther` | str | 4,877 |  |
| `parq.ortho.rightShoulder[]` | str | 4,320 | `None` (3408); `Other` (561); `Weakness` (190); `Rotator Cuff` (182); `Decreased ROM` (138); `Arthritis` (88); `Tendonitis` (59); `Surgery` (55); `Replacement` (30); `Labral Tear` (24); `Laberal Tear` (23) |
| `parq.ortho.rightWrist` | array | 4,877 |  |
| `parq.ortho.rightWristOther` | str | 4,877 |  |
| `parq.ortho.rightWrist[]` | str | 4,291 | `None` (3788); `Other` (316); `Carpal Tunnel` (124); `Broken` (89); `Tendinitis` (58); `Sprained` (34) |

## `reassessmentComments`

| Path | Type | Docs | Values (closed lists only) |
|---|---|---|---|
| `reassessmentComments` | object | 3,877 |  |
| `reassessmentComments.bodyAssessmentComment` | str | 3,877 |  |
| `reassessmentComments.fitnessAssessmentComment` | str | 3,876 |  |

## Fitness exercises

Every `fitnessAssessment.program.<exercise>` has the same fields as the `<exercise>` rows above
(`bandCompany`, `colourBand`, `colourName`, `observation[]`, `other`, `score`). Each
`fitnessAssessment.test.<test>` has `reps` and `timing`; some tests also have `observation[]` and `other`.
In the tables above, document counts on `<exercise>` rows are for `squats` and on `<test>` rows are for `pushUp`.

| Exercise | Docs | Observation options |
|---|---|---|
| `agilityLadder` | 3,440 | `Other` (59); `Coachable` (43); `Poor Coordination` (33); `Out of Breath` (17); `None` (12); `Out Of Breath` (7) |
| `bearCrawl` | 3,440 | `None` (75); `Coachable` (45); `Lateral Shifting` (34); `Other` (34); `Poor Coordination` (29); `Poor ROM` (26); `Forward Motion Only` (16) |
| `floorDownUp` | 3,496 | `Other` (80); `None` (75); `Challenging` (69); `Needs Aid` (66); `Coachable` (49) |
| `forwardBend` | 4,012 | `Touched Toes` (546); `Touched Floor` (466); `Touched Shins` (409); `Other` (356); `Bent Knees` (292); `None` (237); `Touched Knees` (189); `Touched Ankles` (141); `Touched Shin` (113); `Touched Ankle` (87) |
| `gait` | 3,496 | `None` (96); `Rounded Shoulders` (86); `Other` (65); `Looks at Floor` (59); `Shuffles Feet` (57); `Needs Aid` (23); `Device(s) Used` (19); `Looks At Floor` (17) |
| `highKnees` | 3,998 | `Coachable` (576); `Other` (475); `None` (444); `Great ROM` (416); `Modified - March` (407); `Out of Breath` (304); `Poor ROM` (197); `Out Of Breath` (71) |
| `jumpingJacks` | 3,379 | `None` (61); `Other` (55); `Poor Arm / Shoulder ROM` (38); `Out of Breath` (34); `No Jump` (31); `Shrugging` (5); `Cross Jacks` (5) |
| `lateralAndPosteriorKicks` | 3,379 | `Coachable` (84); `Poor Glute Activation` (65); `Needs Aid For Balance` (59); `Forward Lean - Posterior Kick` (45); `Other` (44); `Can't Lead With Heel - Lateral Kick` (36); `None` (29) |
| `lateralKicks` | 3,792 | `Coachable` (447); `None` (359); `Poor Glute Activation` (349); `Side Bend / Lean` (331); `Other` (323); `Needs Aid For Balance` (230); `Can't Lead With Heel - Lateral Kick` (221); `Limited ROM` (217); `Bent Leg` (87) |
| `overHeadReach` | 3,379 | `Coachable` (75); `Arms Fall Forward` (64); `Other` (58); `None` (38); `Limited ROM` (38); `Shrugging` (33); `Back Arches` (27) |
| `plank` | 4,012 | `Coachable` (640); `Other` (631); `None` (589); `Shaky` (571); `Hip Hike` (281); `Elevated` (222); `Hips Dip` (178); `Dropped Hips` (134); `Bird Dog` (35) |
| `pushUp` | 3,379 | `Other` (68); `Coachable` (56); `None` (56); `1 / 2 ROM` (55); `On Knees` (36); `Elevated Push Up` (27); `Dropped Hips` (18); `Hip Hike` (13); `Shrugging` (12); `Full ROM` (10); `Quadruped Push Up` (8); `Kneck Movement` (6) |
| `shoulderPress` | 3,998 | `Other` (667); `Coachable` (660); `Arms Fall Forward` (532); `None` (489); `Poor ROM` (247); `Shrugging` (210); `Arching` (158) |
| `shuffle` | 3,379 | `None` (72); `Coachable` (66); `Poor Coordination` (34); `Other` (28); `Out of Breath` (18) |
| `sidePlankRL` | 3,867 | `None` (551); `Other` (457); `Coachable` (351); `Hips Dropped` (229); `Legs Staggered` (211); `Elbow Not Under Shoulder` (117) |
| `sideStep` | 3,496 | `None` (93); `Small Steps` (73); `Other` (54); `Shuffles Feet` (40); `Loses Focus / Rhythm` (32) |
| `singleLegBalanceLeft` | 4,012 | `None` (590); `Ankle Flexion` (397); `Needs Aid` (380); `Other` (361) |
| `singleLegBalanceRight` | 4,012 | `None` (584); `Ankle Flexion` (398); `Other` (377); `Needs Aid` (377) |
| `skaters` | 3,792 | `None` (433); `Coachable` (373); `Other` (236); `No Jump` (199); `Poor Coordination` (184); `Out of Breath` (166); `No Toe Touch` (79); `No SL Balance` (67); `Out Of Breath` (34) |
| `squatSitToStand` | 3,496 | `Coachable` (133); `Other` (128); `Excessive Forward Lean` (77); ` Poor ROM` (60); `Momentum / Swinging` (47); `Needs Aid` (44); `None` (37); `Great ROM` (35); `Valgus` (22); `Forward Lean` (4) |
| `squats` | 3,881 | `Coachable` (894); `Other` (690); ` Excessive Forward Lean` (579); `None` (359); `Poor ROM` (352); `Heels Raised` (337); `Great ROM` (288); `Pronated Feet` (182); `Rounding` (172); `Valgus` (131); `Arching` (96) |
| `standingCrossCrunch` | 3,379 | `None` (77); `Coachable` (55); `Other` (31); `Poor Cross Rotation` (29); `Poor Range Of Motion` (28); `No Hip Rotation` (19); `Unable To Reach Hands To Ears` (10) |
| `standingRow` | 3,867 | `Coachable` (514); `None` (478); `Other` (392); `Rounded Shoulders` (292); `Shrugging` (252) |

| Test | Docs | `timing` values | Observation options |
|---|---|---|---|
| `alternateHealTouch` | 4,072 | `0` (1814); `""` (1353); `30` (104); `15` (33); `60` (9); `45` (3) | `None` (72); `Other` (60); `Couldn't Touch Fingers To Heels` (42); ` Poor Coordination` (22); `Didn't Comprehend Exercise` (9); `Couldn't Touch Fingers to Heels` (2) |
| `bigArmCircles` | 4,072 | `0` (1800); `""` (1349); `30` (115); `15` (45); `45` (6); `60` (2) | `Arms Lowered Over Time` (66); `None` (59); `Big Circles Become Small Circles` (58); `Other` (54); `Loses Focus` (41); `Poor Coordination` (29) |
| `chairSitToStand` | 4,215 | `0` (1776); `""` (1371); `30` (271); `15` (42); `60` (7); `45` (5) | `Forward Lean` (101); `Other` (78); `None` (67); `Momentum / Swinging` (57); `Needs Aid` (52); `Valgus` (3) |
| `dominantSeatedArmCurl` | 4,215 | `0` (1793); `""` (1379); `30` (246); `15` (39); `45` (8); `60` (8) | `N/A` (59); `Men (8 Lbs)` (8); `Other` (6); `None` (5) |
| `elevatedPushUp` | 4,215 | `0` (1787); `""` (1376); `30` (252); `15` (48); `60` (5) | `Other` (99); `Full ROM` (65); `1 / 2 ROM` (64); `None` (57); `Neck Movement` (37); `Shrugging` (32); `Dropped Hips` (31); `1 / 4 ROM` (17) |
| `frogJump` | 4,139 | `0` (1792); `""` (1369); `30` (174); `15` (43); `60` (10); `45` (6) | `Out of Breath` (98); `None` (68); `Forward Lean` (53); `Poor Form` (46); `Other` (44); `Poor Ankle Mobility` (36); `Not Full ROM` (34); `Stays on Toes` (31); `No Jump` (23); `No Arm Swing` (22); `Valgus` (11) |
| `lateralJump` | 4,072 | `0` (1828); `""` (1349); `30` (93); `15` (39); `60` (8); `45` (2) | `None` (100); `Out of Breath` (48); `Other` (36); `Poor Coordination` (27) |
| `plankOrShoulderTouch` | 4,694 | `30` (1435); `""` (1223); `0` (1168); `15` (352); `45` (64); `60` (30) | `Lateral Hip Shift` (802); `Elevated Hips` (474); `None` (468); `Other` (394); `Hands Not Under Shoulders` (228); `From Knees` (183) |
| `pushUp` | 4,694 | `30` (1673); `""` (1188); `0` (946); `15` (408); `45` (53); `60` (36) | `On Knees` (714); `Other` (661); `1 / 2 ROM` (622); `Full ROM` (336); `None` (312); `Dropped Hips` (196); `Shrugging` (188); `1 / 4 ROM` (175); `Neck Movement` (156) |
| `s2sEnduranceJump` | 4,694 | `30` (1483); `""` (1201); `0` (1152); `15` (311); `45` (70); `60` (57) | `None` (726); `Out of Breath` (548); `Other` (361); `Poor Coordination` (198); `Poor Form` (122); `Poor form` (26) |
| `sitToStand` | 4,072 | `0` (1796); `""` (1355); `30` (125); `15` (41); `45` (2) | `None` (63); `Other` (54); `Excessive Forward Lean` (39); `Momentum / Swinging` (22); `Needs Aid` (21); `Valgus` (9); `Forward Lean` (4) |
| `squatJump` | 4,607 | `30` (1280); `0` (1249); `""` (1210); `15` (327); `45` (54); `60` (22) | `Out of Breath` (554); `None` (391); `Other` (341); `Forward Lean` (322); `1 / 2 ROM` (260); `Stays on Toes` (217); `No Jump` (153); `Deep Squat` (134); `No Arm Swing` (119); `1 / 4 ROM` (96); `Valgus` (57) |
| `stepTest` | 4,215 | `0` (1794); `""` (1376); `30` (249); `15` (42); `60` (7); `45` (5) | `None` (117); `Other` (78); `Needs Aid` (50); `Out of Breath` (42) |



|  data quality issue  | description                               | affected_files                                                                 | example                                           | solution                             |
| :------------------: | ----------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------- | ------------------------------------ |
|  Dictionary Strings  | Dictionaries stored as strings            | "weapons.csv", "weapons_upgrades.csv", "armors.csv", "bosses.csv", "ammos.csv" | `{'Str': 15, 'Dex': 14}`                          | Use regex or ast.literal_eval()      |
| Null Representations | Multiple ways to represent missing values | ["'-'", "'N/A'", "''", "'null'", "'None'", "empty string"]                     | All files                                         | Standardize to NULL                  |
|     List Strings     | Lists stored as strings                   | ["creatures.csv", "locations.csv", "cookbooks.csv"]                            | ['item1', 'item2', 'item3']                       | Parse and explode                    |
|  Number Formatting   | Numbers with commas or as strings         | "bosses.csv (HP, runes)", "items/remembrances.csv (value)"                     | '6,080' or '120,000'                              | Remove commas and cast to integer    |
|  Nested Structures   | Lists of dictionaries                     | "armors.csv (damage_negation, resistance)"                                     | [{'Phy': '1.8', 'Mag': '5.0'}]                    | Parse list[0] then parse dictionary  |
|  Complex HP Values   | Single or multi-phase HP                  | bosses.csv                                                                     | 7,560 (phase 1) 13,608 (phase 2) 13,608 (phase 3) | Extract phases separately with regex |

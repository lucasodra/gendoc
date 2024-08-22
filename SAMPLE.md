
```json
[
    {
        "title": "Wills",
        "sections": [
            {
                "order": 1,
                "sectionName": "Introduction",
                "type": "generate-once",
                "subtitle": "Introduction",
                "sections": [],
                "inputType": {
                    "type": "string",
                    "name": "string",
                    "identificationNo": "string",
                    "address": "string"
                },
                "constructors": [
                    {
                        "type": "international",
                        "fields": ["name", "identificationNo", "address"],
                        "clause": "I, [name] [identificationNo], of [addess], HEREBY REVOKE all former wills, codicils and testamentary dispositions hereinbefore made by me AND DECLARE this to be my Last Will and Testament (hereinafter called my “Will”). This Will covers all my movable and immovable property whatsoever and wheresoever situate which I may be possessed of or entitled to at my death (including any property over which I may have a power of appointment or disposition by will)."
                    },
                    {
                        "type": "singapore",
                        "fields": ["name", "identificationNo", "address"],
                        "clause": "I [name] [identificationNo], of [address], HEREBY REVOKE all former wills and testamentary dispositions made by me in relation to all my immovable and movable property in Singapore only and I DECLARE this to be my last Will relating thereto (hereinafter called my “Will”). I expressly DECLARE that I do not revoke any wills or testamentary dispositions made by me other than in relation to my immovable and movable property in Singapore, and further DECLARE that this Will shall be read, construed and proved independently of any will or wills which I have made or may make in respect of my assets outside of Singapore and shall not affect any other will or wills which I have made or may make in respect of my assets outside of Singapore."
                    }
                ]
            },
            {
                "order": 2,
                "sectionName": "Executors",
                "type": "generate-once",
                "subtitle": "Executors",
                "sections": [
                    {
                        "order": 1,
                        "sectionName": "Primary Executors",
                        "type": "generate-once",
                        "subtitle": "",
                        "sections": [],
                        "inputType": {
                            "type": "string",
                            "uen": "string",
                            "name": "string",
                            "identificationNo": "string",
                            "address": "string",
                            "executors": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "name": "string",
                                        "identificationNo": "string",
                                        "address": "string"
                                    }
                                }
                            }
                        },
                        "constructors": [
                            {
                                "type": "sole-person",
                                "fields": ["name", "identificationNo", "address"],
                                "clause": "I APPOINT [name] [identificationNo], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
                            },
                            {
                                "type": "sole-person",
                                "fields": ["name", "identificationNo"],
                                "clause": "I APPOINT [name] [identificationNo] to be the sole executor of this my Will (hereinafter called “my Executor”)."
                            },
                            {
                                "type": "sole-person",
                                "fields": ["name", "address"],
                                "clause": "I APPOINT [name], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
                            },
                            {
                                "type": "sole-entity",
                                "fields": ["name", "uen", "address"],
                                "clause": "I APPOINT [name] [uen], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
                            },
                            {
                                "type": "sole-entity",
                                "fields": ["name", "uen"],
                                "clause": "I APPOINT [name] [uen] to be the sole executor of this my Will (hereinafter called “my Executor”)."
                            },
                            {
                                "type": "joint",
                                "fields": ["executors"],
                                "clause": "I APPOINT {{#each executors}}[{{this.name}}] [{{this.identificationNo}}], of [{{this.address}}]{{#unless @last}}, {{/unless}}{{/each}} to be the joint executors of this my Will (hereinafter called “my Executors”)."
                            }
                        ]
                    },
                    {
                        "order": 2,
                        "sectionName": "Replacement Executors",
                        "type": "generate-multiple",
                        "subtitle": "Replacement Executors",
                        "sections": [],
                        "inputType": {
                            "replacementExecutors": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "name": "string",
                                        "identificationNo": "string",
                                        "address": "string"
                                    }
                                }
                            },
                            "actingMethod": {
                                "type": "string",
                                "enum": ["solely", "jointly", "jointly and severally"]
                            }
                        },
                        "constructors": [
                            {
                                "type": "replacement-sole-person",
                                "fields": ["replacementExecutors[0].name", "replacementExecutors[0].identificationNo", "replacementExecutors[0].address"],
                                "clause": "If the above-named executor or executors shall predecease me or shall be unable to act, then and only then I APPOINT [replacementExecutors[0].name] [replacementExecutors[0].identificationNo], of [replacementExecutors[0].address] as the replacement executor of this my Will who shall act [actingMethod]."
                            },
                            {
                                "type": "replacement-sole-person",
                                "fields": ["replacementExecutors[0].name", "replacementExecutors[0].identificationNo"],
                                "clause": "If the above-named executor or executors shall predecease me or shall be unable to act, then and only then I APPOINT [replacementExecutors[0].name] [replacementExecutors[0].identificationNo] as the replacement executor of this my Will who shall act [actingMethod]."
                            },
                            {
                                "type": "replacement-sole-person",
                                "fields": ["replacementExecutors[0].name", "replacementExecutors[0].address"],
                                "clause": "If the above-named executor or executors shall predecease me or shall be unable to act, then and only then I APPOINT [replacementExecutors[0].name], of [replacementExecutors[0].address] as the replacement executor of this my Will who shall act [actingMethod]."
                            },
                            {
                                "type": "replacement-joint",
                                "fields": ["replacementExecutors", "actingMethod"],
                                "clause": "If the above-named executor or executors shall predecease me or shall be unable to act, then and only then I APPOINT {{#each replacementExecutors}}[{{this.name}}] [{{this.identificationNo}}], of [{{this.address}}]{{#unless @last}}, {{/unless}}{{/each}} as the replacement executor/s of this my Will who shall act [actingMethod]. I declare that in this Will, the expression 'my executor/s' shall, where the context admits, include the replacement executor/s of this Will."
                            }
                        ]
                    },
                    {
                        "order": 3,
                        "sectionName": "Empowerment to Appoint Replacement Executors",
                        "type": "generate-once",
                        "subtitle": "Empowerment Clause",
                        "sections": [],
                        "inputType": {
                            "empowermentOption": {
                                "type": "boolean",
                                "description": "Indicates whether the executor is empowered to appoint a replacement."
                            },
                            "professionalTrustee": {
                                "type": "string",
                                "description": "Optional field for specifying a professional trustee or trust company."
                            }
                        },
                        "constructors": [
                            {
                                "type": "empowerment-clause",
                                "fields": ["empowermentOption", "professionalTrustee"],
                                "clause": "If the above-named executor shall be unable to act for any reason, I EMPOWER my executor/s to appoint a suitable replacement executor, including a professional trustee such as [professionalTrustee]. I declare that in this Will, the expression 'my executor/s' shall, where the context admits, include the replacement executor/s of this Will."
                            },
                            {
                                "type": "empowerment-clause",
                                "fields": ["empowermentOption"],
                                "clause": "If the above-named executor shall be unable to act for any reason, I EMPOWER my executor/s to appoint a suitable replacement executor. I declare that in this Will, the expression 'my executor/s' shall, where the context admits, include the replacement executor/s of this Will."
                            }
                        ]
                    }
                ]
            }
        ]
        
    }
]
```


// [
//     {
//         "title": "Wills",
//         "sections": [
//             {
//                 "order": 1,
//                 "type": "generate-once",
//                 "name": "Introduction",
//                 "sections": [],
//                 "inputIntegrity": {
//                     "type": "required",
//                     "name": "required",
//                     "identificationNo": {
//                         "integrity": "optional-but-required-if",
//                         "present-any": [],
//                         "absent-any": ["address"],
//                         "present-all": "",
//                         "absent-all": "address"
//                     },
//                     "address": "optional"
//                 },
//                 "inputType": {
//                     "type": "string",
//                     "name": "string",
//                     "identificationNo": "string",
//                     "address": "string"
//                 },
//                 "constructors": [
//                     {
//                         "type": "international",
//                         "fields": ["name", "identificationNo", "address"],
//                         "clause": "I, [name] [identificationNo], of [addess], HEREBY REVOKE all former wills, codicils and testamentary dispositions hereinbefore made by me AND DECLARE this to be my Last Will and Testament (hereinafter called my “Will”). This Will covers all my movable and immovable property whatsoever and wheresoever situate which I may be possessed of or entitled to at my death (including any property over which I may have a power of appointment or disposition by will)."
//                     },
//                     {
//                         "type": "singapore",
//                         "fields": ["name", "identificationNo", "address"],
//                         "clause": "I [name] [identificationNo], of [address], HEREBY REVOKE all former wills and testamentary dispositions made by me in relation to all my immovable and movable property in Singapore only and I DECLARE this to be my last Will relating thereto (hereinafter called my “Will”). I expressly DECLARE that I do not revoke any wills or testamentary dispositions made by me other than in relation to my immovable and movable property in Singapore, and further DECLARE that this Will shall be read, construed and proved independently of any will or wills which I have made or may make in respect of my assets outside of Singapore and shall not affect any other will or wills which I have made or may make in respect of my assets outside of Singapore."
//                     }
//                 ]
//             },
//             {
//                 "order": 2,
//                 "subtitle": "Executors",
//                 "sections": [
//                     {
//                         "order": 2,
//                         "type": "generate-once",
//                         "subtitle": "",
//                         "inputIntegrity": {
//                             "type": "required",
//                             "name": "required",
//                             "uen": {
//                                 "integrity": "optional-if",
//                                 "variable": "type",
//                                 "comparison": "equals",
//                                 "reference": "entity"
//                             },
//                             "identificationNo": [
//                                 {
//                                     "integrity": "required-if",
//                                     "variable": "type",
//                                     "comparison": "equals",
//                                     "reference": "person"
//                                 },
//                                 {
//                                     "integrity": "required-if",
//                                     "present-any": [],
//                                     "absent-any": ["address"],
//                                     "present-all": "",
//                                     "absent-all": "address"
//                                 }],
//                             "address": "optional"
//                         },
//                         "inputType": {
//                             "type": "string",
//                             "name": "string",
//                             "uen": "string",
//                             "identificationNo": "string",
//                             "address": "string"
//                         },
//                         "constructors": [
//                             {
//                                 "type": "person",
//                                 "fields": ["name", "identificationNo", "address"],
//                                 "clause": "I APPOINT [name] [identificationNo], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "person",
//                                 "fields": ["name", "identificationNo"],
//                                 "clause": "I APPOINT [name] [identificationNo], to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "person",
//                                 "fields": ["name", "address"],
//                                 "clause": "I APPOINT [name], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "entity",
//                                 "fields": ["name", "uen", "address"],
//                                 "clause": "I APPOINT [name] [uen], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "entity",
//                                 "fields": ["name", "uen"],
//                                 "clause": "I APPOINT [name] [uen], to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "entity",
//                                 "fields": ["name", "address"],
//                                 "clause": "I APPOINT [name], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             }
//                         ]
//                     },
//                     {
//                         "order": 3,
//                         "type": "generate-multiple",
//                         "subtitle": "Replacement Executors",
//                         "inputIntegrity": {
//                             "type": "required",
//                             "name": "required",
//                             "uen": {
//                                 "integrity": "optional-if",
//                                 "variable": "type",
//                                 "comparison": "equals",
//                                 "reference": "entity"
//                             },
//                             "identificationNo": [
//                                 {
//                                     "integrity": "required-if",
//                                     "variable": "type",
//                                     "comparison": "equals",
//                                     "reference": "person"
//                                 },
//                                 {
//                                     "integrity": "required-if",
//                                     "present-any": [],
//                                     "absent-any": ["address"],
//                                     "present-all": "",
//                                     "absent-all": "address"
//                                 }],
//                             "address": "optional"
//                         },
//                         "inputType": {
//                             "type": "string",
//                             "name": "string",
//                             "identificationNo": "string",
//                             "address": "string"
//                         },
//                         "constructors": [
//                             {
//                                 "type": "person",
//                                 "fields": ["name", "identificationNo", "address"],
//                                 "clause": "I APPOINT [name] [identificationNo], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "person",
//                                 "fields": ["name", "identificationNo"],
//                                 "clause": "I APPOINT [name] [identificationNo], to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "person",
//                                 "fields": ["name", "address"],
//                                 "clause": "I APPOINT [name], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "entity",
//                                 "fields": ["name", "uen", "address"],
//                                 "clause": "I APPOINT [name] [uen], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "entity",
//                                 "fields": ["name", "uen"],
//                                 "clause": "I APPOINT [name] [uen], to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             },
//                             {
//                                 "type": "entity",
//                                 "fields": ["name", "address"],
//                                 "clause": "I APPOINT [name], of [address] to be the sole executor of this my Will (hereinafter called “my Executor”)."
//                             }
//                         ]
//                     }
//                 ]
//             }
//         ]
        
//     }
// ]
Objective : Change patient so that it is trapped by measure CMS62V2

Action : Create a patient 
Impact : An entry is created in Record Collection
[JSON](https://github.com/dheeti/beatdoc/blob/master/files/demo_test3_v0_created.json)

Action : Check/Uncheck boxes for IPP/DENOM/Numer
Impact : Respective fields set to 1 in expected_values collection
[JSON](https://github.com/dheeti/beatdoc/blob/master/files/demo_test3_v1_IPPChecked.json)

Action : 
Added "Encounter:Performed HIV Visit". No values were changed.
Impact : 
a.An entry is created in source_data_criteria collection with following values

    "source_data_criteria" : [         
     {
            "negation" : false,
            "definition" : "encounter",
            "status" : "performed",
            "title" : "HIV Visit",
            "description" : "Encounter, Performed: HIV Visit",
            "code_list_id" : "2.16.840.1.113883.3.464.1003.101.12.1047",
            "type" : "encounters",
            "id" : "EncounterPerformedHivVisit",
            "start_date" : NumberLong(1331625600000),
            "end_date" : NumberLong(1331626500000),
            "value" : [],
            "references" : null,
            "field_values" : {},
            "hqmf_set_id" : "F70B2984-AF4A-4072-AE0D-CEC677A7FF8F",
            "cms_id" : "CMS62v2",
            "criteria_id" : "14c116bb4f6ui",
            "codes" : {
                "CPT" : [ 
                    "99392"
                ],
                "SNOMED-CT" : [ 
                    "12843005"
                ]
            },
            "negation_code_list_id" : "",
            "coded_entry_id" : ObjectId("550269786a61795bd31e0000"),
            "code_source" : "DEFAULT"
        }, 

b. An entry is created under encounters collection with value 

    "encounters" : [ 
        {
            "_id" : ObjectId("550269786a61795bd31e0000"),
            "codes" : {
                "CPT" : [ 
                    "99392"
                ],
                "SNOMED-CT" : [ 
                    "12843005"
                ]
            },
            "mood_code" : "EVN",
            "_type" : "Encounter",
            "description" : "Encounter, Performed: HIV Visit",
            "start_time" : 1331625600,
            "end_time" : 1331626500,
            "status_code" : {
                "HL7 ActStatus" : [ 
                    "performed"
                ]
            },
            "oid" : "2.16.840.1.113883.3.560.1.79"
        }
    ],

[JSON](https://github.com/dheeti/beatdoc/blob/master/files/demo_test3_v2_AddEncounterPerformed.json)

Action : Added Diagnosis : Active HIV 
Impact : 
a. An entry is created in "source_data_criteria" collection

        {
            "negation" : false,
            "definition" : "diagnosis",
            "status" : "active",
            "title" : "HIV",
            "description" : "Diagnosis, Active: HIV",
            "code_list_id" : "2.16.840.1.113883.3.464.1003.120.12.1003",
            "type" : "conditions",
            "id" : "DiagnosisActiveHiv",
            "start_date" : NumberLong(1331625600000),
            "end_date" : NumberLong(1331626500000),
            "value" : [],
            "references" : null,
            "field_values" : {},
            "hqmf_set_id" : "F70B2984-AF4A-4072-AE0D-CEC677A7FF8F",
            "cms_id" : "CMS62v2",
            "criteria_id" : "14c11766ee9SK",
            "codes" : {
                "SNOMED-CT" : [ 
                    "111880001"
                ],
                "ICD-10-CM" : [ 
                    "Z21"
                ],
                "ICD-9-CM" : [ 
                    "V08"
                ]
            },
            "negation_code_list_id" : "",
            "coded_entry_id" : ObjectId("55026c2a6a61795bd3260000"),
            "code_source" : "DEFAULT"
        }, 

b. A new field called as "conditions" is inserted with following values

    "conditions" : [ 
        {
            "_id" : ObjectId("55026c2a6a61795bd3260000"),
            "codes" : {
                "SNOMED-CT" : [ 
                    "111880001"
                ],
                "ICD-10-CM" : [ 
                    "Z21"
                ],
                "ICD-9-CM" : [ 
                    "V08"
                ]
            },
            "mood_code" : "EVN",
            "_type" : "Condition",
            "description" : "Diagnosis, Active: HIV",
            "start_time" : 1331625600,
            "end_time" : 1331626500,
            "status_code" : {
                "SNOMED-CT" : [ 
                    "55561003"
                ],
                "HL7 ActStatus" : [ 
                    "active"
                ]
            },
            "oid" : "2.16.840.1.113883.3.560.1.2"
        }
    ],

[JSON][https://github.com/dheeti/beatdoc/blob/master/files/demo_test3_v3_AddDiagnosisActiveHIV.json]

Action : Addded Encounter Performed : HIV Visit. This encounter was performed 90 days after 1st Encounter

Impact : New Entry created in collection "source_data_criteria" with following values

        {
            "negation" : false,
            "definition" : "encounter",
            "status" : "performed",
            "title" : "HIV Visit",
            "description" : "Encounter, Performed: HIV Visit",
            "code_list_id" : "2.16.840.1.113883.3.464.1003.101.12.1047",
            "type" : "encounters",
            "id" : "EncounterPerformedHivVisit",
            "start_date" : NumberLong(1355904000000),
            "end_date" : NumberLong(1356682500000),
            "value" : [],
            "references" : null,
            "field_values" : {},
            "hqmf_set_id" : "F70B2984-AF4A-4072-AE0D-CEC677A7FF8F",
            "cms_id" : "CMS62v2",
            "criteria_id" : "14c118027843G",
            "codes" : {
                "CPT" : [ 
                    "99392"
                ],
                "SNOMED-CT" : [ 
                    "12843005"
                ]
            },
            "negation_code_list_id" : "",
            "coded_entry_id" : ObjectId("55026eb86a61795bd33e0000"),
            "code_source" : "DEFAULT"
        }, 

[JSON]([https://github.com/dheeti/beatdoc/blob/master/files/demo_test3_v4_AddEncounterPerformed90DaysLater.json)

Now all Measure Conditions are GREEN
Checking & Unchecking Checkboxes for IPP, DENOM, Numer impacts values in records.expected_values collection

Action : 
Added "Encounter:Performed HIV Visit". No values were changed.
Impact : 
a.An entry is created in source_data_criteria collection with following values

'''

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

'''

b. An entry is created under encounters collection with value 

'''

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

'''
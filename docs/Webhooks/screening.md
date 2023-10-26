# Screening

Some webhooks are sent from Turn to your system on specific events, here is the listing of those webhooks, how to configure them, and what the responses look like.

## a) Candidate status update

The _Candidate Status Update Webhook_ is triggered when a candidate of yours is moved from one status to another. Let's consider a common flow:

* From emailed to consent
* From consent to processing
* From processing to pending
* From pending to approved

In this case, 4 webhooks would be triggered one for each status change.

### Webhook content

```javascript
{
  "team_member_email": "contact@turning.io",
  "original_state": "pending",
  "dashboard_url": "http://partners.turning.io/workers/623580e8-9a76-462f-acc9-2a190be182fa",
  "event_id": "11c42854-364e-481e-8e9b-22c21e9edeea",
  "state": "approved",
  "timestamp": 1527800278,
  "worker_email": "alec@sadtech.ca",
  "worker_id": "623580e8-9a76-462f-acc9-2a190be182fa",
  "consent_date": '2022-09-15',
  "recheck_date": '2023-01-10',
  "cm_criminal_enroll": '2023-07-19',
  "criminal_monitoring_triggered": true
}
```

This table maps out the Dashboard background check status with it's corresponding webhook status.

| Dashboard Status  | API Status             |
|-------------------|------------------------|
| Emailed           | emailed                |
| Processing        | processing             |
| Reviewing         | review                 |
| Verifying         | review__identity       |
| Consent           | consent                |
| Consider          | pending                |
| Approved          | approved               |
| Compliance Review | review__so             |
| Compliance Review | review__qa             |
| Compliance Review | review__mvr            |
| Compliance Review | review__cm             |
| Rejected          | rejected               |
| First Notice      | pending__first_notice  |
| Second Notice     | pending__second_notice |
| Withdrawn         | withdrawn              |
| Initiated         | initiated              |

## b) Background Check Results

The _Background Check Result webhook_ is triggered when an API initiated background check is completed, this means that the results are available and the status of check is either `approved`  or `pending`. The endpoints that trigger are: 

/person/search_async
/fcra_check/form/:check_id

Both endpoints use a `callback_url` input parameter which will be used to deliver the webhook.

### Webhook content

```javascript
{
  "checks": {
    "location": null,
    "addresses": [
      {
        "address1": "2195 Harris Heights Suite 287",
        "county": "South Lauren County",
        "state": "MD",
        "zip": "38942",
        "city": "Lake Hollystad",
        "zip4": "8705"
      }
    ],
    "aliases": null,
    "criminal": [
      {
        "county": "Other Counties",
        "value": [
          {
            "ssn": null,
            "first_name_match": "ExactMatch",
            "suspect_middle_name": null,
            "gender": null,
            "disposition_date": "09-11-2018",
            "height": null,
            "date_of_birth_match": "ExactMatch",
            "charges_filed_date": null,
            "case_number": "6721",
            "county": null,
            "other_addresses": null,
            "hair": null,
            "weight": null,
            "last_name_match": "ExactMatch",
            "eyes": null,
            "id": "JIRElFWSBZqK34cJ1h_seKFJVaUqRJ4=",
            "address_match": "ExactMatch",
            "crime_type": "Misdemeanor",
            "suspect_state": "MO",
            "drivers_license_number": null,
            "middle_name_match": null,
            "birth_address": null,
            "offense_description_1": "Skill imagine method system.",
            "offense_date": "03-22-2016",
            "other_dates_of_birth": null,
            "sentence": null,
            "suspect_county": null,
            "suspect_first_name": "Chelsea",
            "arrest_date": null,
            "suspect_last_name": null,
            "disposition": "Guilty",
            "violation_date": null,
            "conviction_date": null,
            "a_k_as": null
          },
          {
            "ssn": null,
            "first_name_match": "ExactMatch",
            "suspect_middle_name": null,
            "gender": null,
            "disposition_date": "09-11-2018",
            "height": null,
            "date_of_birth_match": "ExactMatch",
            "charges_filed_date": null,
            "case_number": "5957",
            "county": null,
            "other_addresses": null,
            "hair": null,
            "weight": null,
            "last_name_match": "ExactMatch",
            "eyes": null,
            "id": "DMAfJ7RwDYMkUIKsge1O5RYz1AZXt08=",
            "address_match": "ExactMatch",
            "crime_type": "Misdemeanor",
            "suspect_state": "SC",
            "drivers_license_number": null,
            "middle_name_match": null,
            "birth_address": null,
            "offense_description_1": "Visit knowledge play provide.",
            "offense_date": "03-22-2016",
            "other_dates_of_birth": null,
            "sentence": null,
            "suspect_county": null,
            "suspect_first_name": "Chelsea",
            "arrest_date": null,
            "suspect_last_name": null,
            "disposition": "Guilty",
            "violation_date": null,
            "conviction_date": null,
            "a_k_as": null
          },
          {
            "ssn": null,
            "first_name_match": "ExactMatch",
            "suspect_middle_name": null,
            "gender": null,
            "disposition_date": "09-11-2018",
            "height": null,
            "date_of_birth_match": "ExactMatch",
            "charges_filed_date": null,
            "case_number": "398",
            "county": null,
            "other_addresses": null,
            "hair": null,
            "weight": null,
            "last_name_match": "ExactMatch",
            "eyes": null,
            "id": "c2yysgwMRow8Ey-7CJiXPNnqQHYHK5s=",
            "address_match": "ExactMatch",
            "crime_type": "Misdemeanor",
            "suspect_state": "NC",
            "drivers_license_number": null,
            "middle_name_match": null,
            "birth_address": null,
            "offense_description_1": "Save attack happy yard.",
            "offense_date": "03-22-2016",
            "other_dates_of_birth": null,
            "sentence": null,
            "suspect_county": null,
            "suspect_first_name": "Chelsea",
            "arrest_date": null,
            "suspect_last_name": null,
            "disposition": "Guilty",
            "violation_date": null,
            "conviction_date": null,
            "a_k_as": null
          },
          {
            "ssn": null,
            "first_name_match": "ExactMatch",
            "suspect_middle_name": null,
            "gender": null,
            "disposition_date": "09-11-2018",
            "height": null,
            "date_of_birth_match": "ExactMatch",
            "charges_filed_date": null,
            "case_number": "2031",
            "county": null,
            "other_addresses": null,
            "hair": null,
            "weight": null,
            "last_name_match": "ExactMatch",
            "eyes": null,
            "id": "R4fISs42O2fzYbSVTpa7rQsWc2d6gw==",
            "address_match": "ExactMatch",
            "crime_type": "Misdemeanor",
            "suspect_state": "FL",
            "drivers_license_number": null,
            "middle_name_match": null,
            "birth_address": null,
            "offense_description_1": "Radio morning outside.",
            "offense_date": "03-22-2016",
            "other_dates_of_birth": null,
            "sentence": null,
            "suspect_county": null,
            "suspect_first_name": "Chelsea",
            "arrest_date": null,
            "suspect_last_name": null,
            "disposition": "Guilty",
            "violation_date": null,
            "conviction_date": null,
            "a_k_as": null
          },
          {
            "ssn": null,
            "first_name_match": "ExactMatch",
            "suspect_middle_name": null,
            "gender": null,
            "disposition_date": "09-11-2018",
            "height": null,
            "date_of_birth_match": "ExactMatch",
            "charges_filed_date": null,
            "case_number": "514",
            "county": null,
            "other_addresses": null,
            "hair": null,
            "weight": null,
            "last_name_match": "ExactMatch",
            "eyes": null,
            "id": "siRMTjCN9nCFD2mdYYIXIDnwJI9xAivk",
            "address_match": "ExactMatch",
            "crime_type": "Infraction",
            "suspect_state": "ID",
            "drivers_license_number": null,
            "middle_name_match": null,
            "birth_address": null,
            "offense_description_1": "Social trip assume tax suddenly.",
            "offense_date": "03-22-2016",
            "other_dates_of_birth": null,
            "sentence": null,
            "suspect_county": null,
            "suspect_first_name": "Chelsea",
            "arrest_date": null,
            "suspect_last_name": null,
            "disposition": "Guilty",
            "violation_date": null,
            "conviction_date": null,
            "a_k_as": null
          },
          {
            "ssn": null,
            "first_name_match": "ExactMatch",
            "suspect_middle_name": null,
            "gender": null,
            "disposition_date": "09-11-2018",
            "height": null,
            "date_of_birth_match": "ExactMatch",
            "charges_filed_date": null,
            "case_number": "562",
            "county": null,
            "other_addresses": null,
            "hair": null,
            "weight": null,
            "last_name_match": "ExactMatch",
            "eyes": null,
            "id": "Kjm_ibdWA6EHna0_9fa9ajP67dQgH7Y=",
            "address_match": "ExactMatch",
            "crime_type": "Felony",
            "suspect_state": "RI",
            "drivers_license_number": null,
            "middle_name_match": null,
            "birth_address": null,
            "offense_description_1": "Bit they father realize could.",
            "offense_date": "03-22-2016",
            "other_dates_of_birth": null,
            "sentence": null,
            "suspect_county": null,
            "suspect_first_name": "Chelsea",
            "arrest_date": null,
            "suspect_last_name": null,
            "disposition": "Guilty",
            "violation_date": null,
            "conviction_date": null,
            "a_k_as": null
          }
        ],
        "status": "ready",
        "clear_eta": null,
        "hit_eta": null
      }
    ],
    "mvr": {
      "accidents": [
        {
          "fault": null,
          "num_vehicles": null,
          "commercial": null,
          "locations": [],
          "plate_number": "436NUB",
          "mvr_record": 301,
          "hazmat": null,
          "accident_death": null,
          "acd_code": null,
          "state_points": null,
          "fr_report": null,
          "property_damage": null,
          "descriptions": [],
          "property_damage_desc": null,
          "id": 199,
          "state": "KY",
          "accident_details": "Again.",
          "incident_date": null,
          "state_code": null,
          "accident_injury": null,
          "accident_injury_num": null
        }
      ],
      "actions": [
        {
          "mail_date": "2019-08-12",
          "action_code": "OS ACTION",
          "actual_end_date": null,
          "additional_messages": [],
          "commercial": null,
          "locations": [],
          "mvr_record": 301,
          "hazmat": null,
          "sub_violations": [],
          "thru_date": null,
          "ordered_date": "2019-08-23",
          "acd_code": null,
          "state_points": null,
          "start_date": "2019-10-20",
          "action_type": "OSWI",
          "descriptions": [
            {
              "state_description": "Mrs eat.",
              "long_description": null,
              "mvr_action": 236,
              "id": 518,
              "mvr_sub_violations": null,
              "mvr_accident": null,
              "short_description": "Good."
            }
          ],
          "end_date": "2019-06-05",
          "id": 236,
          "action_term": null,
          "incident_date": "2019-06-18",
          "state_code": null
        }
      ],
      "driver": {
        "middle_name": null,
        "name_suffix": null,
        "last_name": "Johnston",
        "dob": "2016-09-18",
        "hair_color": null,
        "first_name": "Troy",
        "gender": null,
        "eye_color": null,
        "addresses": [],
        "id": 301,
        "deceased": null,
        "weight": null,
        "height": null,
        "full_name": null,
        "total_state_points": 0,
        "age": 1
      },
      "id": 301,
      "additional_messages": [],
      "licenses": [
        {
          "type_description": "Life TV compare.",
          "classes": [],
          "exp_date": "2019-04-27",
          "issue_date": "2019-05-21",
          "is_valid": false,
          "endorsements": [],
          "has_valid_status": true,
          "surrender_date": null,
          "has_no_surrender_date": true,
          "id": 315,
          "state": "OR",
          "type": "Personal",
          "additional_messages": [],
          "license_number": "9787734443235",
          "mvr_record": 301,
          "statuses": [],
          "has_valid_exp_date": false,
          "original_issue": "War first less."
        }
      ],
      "status": "consider",
      "violations": [
        {
          "adjudications": [],
          "viol_type": "VIOL",
          "fine_amt": "$188083.00",
          "suspension": null,
          "plate_number": "DZG 403",
          "fine_date": null,
          "mvr_record": 301,
          "id": 234,
          "accident": null,
          "fine_state": null,
          "commercial": null,
          "suspension_date": null,
          "locations": [],
          "conviction_date": "2019-03-24",
          "hazmat": null,
          "incident_date": "2019-04-30",
          "sub_violations": [
            {
              "key": "7341",
              "acd_code": "A20",
              "state_points": "8",
              "descriptions": [
                {
                  "state_description": "West.",
                  "long_description": null,
                  "mvr_action": null,
                  "id": 519,
                  "mvr_sub_violations": 274,
                  "mvr_accident": null,
                  "short_description": "Yet."
                }
              ],
              "code_source": "VC",
              "posted_speed": "84",
              "mvr_action": null,
              "id": 274,
              "actual_speed": "54",
              "acd_code_description": "Driving or operating a motor vehicle under the influence of alcohol or drugs",
              "state_code": "YLE7105",
              "incident_num": "0",
              "mvr_violation": 234
            }
          ]
        }
      ]
    },
    "sex_offender": [
      {
        "id": "n0mysdowrhZfMLIKljpj-QAI_mZI2d9D",
        "state": "TN",
        "dispute_status": "not_disputed",
        "offense_description1": null
      }
    ],
    "watchlist": [
      {
        "fax": null,
        "vessel_type": null,
        "marks": null,
        "wanted_by": null,
        "citizenship": null,
        "height": null,
        "score": null,
        "date_of_birth": "1984-06-10",
        "listing_date": null,
        "documents": null,
        "source": "Most Wanted",
        "call_sign": null,
        "remarks": null,
        "address_remarks": null,
        "report_token": "C1931414576",
        "sex": null,
        "tin": null,
        "original_id": null,
        "name": {
          "middle_name": "Derek",
          "name_suffix": null,
          "hash": "5687613933372868694",
          "last_name": "Stewart",
          "first_name": "Chelsea",
          "title": null,
          "professional_suffix": null,
          "id": "GEwEf8YibYMsZyoWoQCApp1_wJaTBg==",
          "date_first_seen": null,
          "date_last_seen": null
        },
        "hair": null,
        "email_address": null,
        "weight": null,
        "vessel_flag": null,
        "page_url": null,
        "dispute_status": "not_disputed",
        "place_of_birth": null,
        "languages": null,
        "political_party": null,
        "legal_basis": null,
        "constituancy": null,
        "website": null,
        "eyes": null,
        "program": null,
        "id": "Iu98a4EsRfZc1B9t5zZJiQUKGlqMFjao",
        "alias_name": null,
        "country": null,
        "tonnage": null,
        "user": 3709,
        "official_title": null,
        "offense": null,
        "grt": null,
        "vessel_owner": null,
        "address": {
          "address_two": null,
          "description": null,
          "hash": "13341304995942013053",
          "date_last_seen": null,
          "report_token": null,
          "address_missing_unit_designation": null,
          "address_one": null,
          "building_name": null,
          "id": "KMHmEw6xFP_zjo2Sfmm5_GLrkshR4uS5",
          "state": null,
          "country_name": "Belize",
          "date_first_seen": null,
          "distance": null,
          "zip4": "99528",
          "subdivision_name": null,
          "address_three": null,
          "city": null,
          "property_photo_address": null,
          "zipcode": "90822"
        },
        "hash": "-17785875946854821044",
        "title": null,
        "phone": null,
        "type": null,
        "image_url": null,
        "full_name": null,
        "alias_type": null
      }
    ],
    "ssn": null,
    "candidate_provided_ssn": null,
    "partner_provided_name": "Todd King",
    "dob_status": "not_matched",
    "public_name_status": "not_matched",
    "name_status": "not_matched",
    "public_record_date_of_birth": "1000-01-01",
    "candidate_provided_name": "Chelsea Derek Stewart",
    "partner_provided_ssn": null,
    "public_provided_name": "No Name Found",
    "ssn_status": "none",
    "candidate_provided_date_of_birth": "1984-06-10"
  },
  "current_address": {
    "address1": "2195 Harris Heights Suite 287",
    "last_seen": "2019-12-19",
    "first_seen": "2019-11-19",
    "state": "MD",
    "zip": "38942",
    "address2": "2513 James Run",
    "city": "Lake Hollystad"
  },
  "date_of_birth": "1984-06-10",
  "name": "Chelsea Derek Stewart",
  "license_number": null,
  "license_state": null,
  "email": "ditto_deborah06@maldonado-wilson.biz",
  "partner_worker_status": "pending",
  "dashboard_url": "https://partners.turn-test.io/workers/07960b8b-0987-4cb6-ac1b-f0d26654d013",
  "turn_id": "C1931414576",
  "reference_id": null,
  "callback_uuid": "a8e385ac-6d3e-40bd-8b8d-d6704290c676",
  "worker_uuid": "07960b8b-0987-4cb6-ac1b-f0d26654d013",
  "consent_date": '2022-09-15',
  "recheck_date": '2023-01-10',
  "cm_criminal_enroll": '2023-07-19',
  "criminal_monitoring_triggered": true
}
```

## c) Consent Confirmation Webhook

When an applicant has successfully consented to their Background Check, you'll receive this webhook notification, this is particularly helpful when your flow involves storing applicants to be run at a later time. 

This notification webhook must be enabled on your account. Please reach out to our Support team to request it be enabled or disabled.

### Webhook content

```javascript
{
    "hook_type": "CONSENT_CONFIRMATION",
    "turn_id": "C1931414576",
    "reference_id":  null,
    "worker_id": "516c5d27-6d1e-4562-8c4c-03ec5faa65fe",
    "consent_date": "2020-08-27 15:07:27.409802",
}
```

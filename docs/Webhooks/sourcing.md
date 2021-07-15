# Sourcing

If you are using Turn's Sourcing product, and you have setup correctly a _Webhook URL_ in your Settings > Integrations section in your Turn Partner Dashboard, the following webhooks describe what events and contents are sent. 

## a) Applicant Sourcing Conversion

The Applicant Sourcing Conversion_ webhook is triggered when an applicant convert (accepts) a Job Invite you initiated via Sourcing. This event is sent for every applicant that converts.


### Webhook content

```javascript
{
  "name": "Hari Seldon",
  "first_name": "Hari",
  "last_name": "Seldon",
  "email": "hari@foundation.io",
  "zipcode": 61601,
  "phone_number": "12345678900",
  "dob": "29/06/1987",
  "state": "CA",
  "city": "San Diego",
  "timestamp": "2020-11-10 00:23:25.884827",
  "event_name": "SOURCING_NEW_CANDIDATE",
  "preferences": {
    "interests": [
      {
        "id": 1,
        "name": "Delivery"
      },
      {
        "id": 2,
        "name": "Moving"
      }
    ],
    "transports": [
      {
        "id": 7,
        "name": "Bike"
      },
      {
        "id": 9,
        "name": "Van"
      }
    ]
  }
}
```

Please note:
* Turn reserves the right to adjust the preferences name(interests and transports), matching by ID is encouraged.
* There could be candidates that choose not to specify this information, so you should be prepared to process an empty list.


## Preferences > Transports Catalog
|id|transport|
|-|:---------:|
|1|Car|
|3|Walk|
|6|Motorcycle|
|7|Bike|
|8|Pickup Truck|
|9|Van|
|2|Box Truck|
|4|Public|

## Preferences > Interests Catalog
|id|interest|
|-|:---------:|
|1	|Delivery|
|3	|Pets|
|4	|Mealsharing|
|5	|Driving|
|6	|Babysitting|
|7	|Home Services|
|9	|Education|
|10	|Creative Services|
|11	|Security|
|12	|Storage|
|13	|Cooking|
|14	|Brand Ambassador|
|15	|Fashion / Beauty|
|16	|Device Repair|
|17	|Personal Training|
|18	|Software Testing|
|19	|Personal Assistant|
|20	|Secret Shopper|
|21	|Tour Guide|
|22	|Real Estate|
|8	|Medical Services|
|2	|Moving|
|24	|Cleaning|
|23	|Caregiving|
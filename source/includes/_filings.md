# Filings

Criminal case filings filed in county or district courts. Use the Filings API calls to request filing information.

## Get Filings

> Example Request:

```shell
curl -H "Content-Type:application/json" -X GET "http://tubmanproject-api.mintyross.com/v1/filings?rundate_min=2018-01-02&rundate_max=2018-01-23&defendant_race=black&current_offense_level_degree=felony"
```

> Example Response:

```json
{
  "success": true,
  "message": "Query successful",
  "data": {
    "metadata": {
      "batch_size": 10000,
      "links": {
        "next": {
          "href": "/v1/filings?query=L3YxL2ZpbGluZ3M_cnVuZGF0ZV9taW49MjAxOC0wMS0wMiZydW5kYXRlX21heD0yMDE4LTAxLTIzJmRlZmVuZGFudF9yYWNlPWJsYWNrJmN1cnJlbnRfb2ZmZW5zZV9sZXZlbF9kZWdyZWU9ZmVsb255_1"
        },
        "self": {
          "href": "/v1/filings?query=L3YxL2ZpbGluZ3M_cnVuZGF0ZV9taW49MjAxOC0wMS0wMiZydW5kYXRlX21heD0yMDE4LTAxLTIzJmRlZmVuZGFudF9yYWNlPWJsYWNrJmN1cnJlbnRfb2ZmZW5zZV9sZXZlbF9kZWdyZWU9ZmVsb255_1"
        }
      },
      "next": "L3YxL2ZpbGluZ3M_cnVuZGF0ZV9taW49MjAxOC0wMS0wMiZydW5kYXRlX21heD0yMDE4LTAxLTIzJmRlZmVuZGFudF9yYWNlPWJsYWNrJmN1cnJlbnRfb2ZmZW5zZV9sZXZlbF9kZWdyZWU9ZmVsb255_1",
      "query": "L3YxL2ZpbGluZ3M_cnVuZGF0ZV9taW49MjAxOC0wMS0wMiZydW5kYXRlX21heD0yMDE4LTAxLTIzJmRlZmVuZGFudF9yYWNlPWJsYWNrJmN1cnJlbnRfb2ZmZW5zZV9sZXZlbF9kZWdyZWU9ZmVsb255_1",
      "total": 89
    },
    "results": [
      {
        "attorney": {
          "connection": {
            "code": "TX",
            "definition": "Y"
          },
          "name": "",
          "spn": ""
        },
        "bond_amount": 888888,
        "calendar_reason": {
          "code": "PACA",
          "definition": "PRELIMINARY ASSIGNED COURT APPEARANCE"
        },
        "case_disposition": {
          "code": "",
          "definition": ""
        },
        "case_number": "157578101010",
        "case_status": {
          "code": "A",
          "definition": "HAS OPEN SETTINGS"
        },
        "court": "232",
        "court_division_indicator": {
          "code": "003",
          "definition": "felony"
        },
        "current_offense": {
          "code": "559906",
          "definition": "POSS CS PG 1 4G - 200G",
          "level_degree": {
            "code": "F2",
            "definition": "FELONY SECOND DEGREE"
          }
        },
        "defendant": {
          "address": {
            "city": "HOUSTON",
            "state": "TX",
            "street_address": "2907 TIDEWATER",
            "street_name": "TIDEWATER",
            "street_number": "2907",
            "zip_code": "77045"
          },
          "birthplace": {
            "code": "",
            "definition": ""
          },
          "date_of_birth": {
            "$date": "1993-05-28T05:00:00Z"
          },
          "name": "MCCARTY, PATRICK WAYNE",
          "race": {
            "code": "B",
            "definition": "BLACK"
          },
          "sex": "M",
          "spn": "02531246"
        },
        "defendant_status": {
          "code": "J",
          "definition": "DEFENDANT WAS PLACED IN A HARRIS COUNTY JAIL"
        },
        "docket_calendar_name": {
          "code": "AC",
          "definition": "ASSIGNED COURT"
        },
        "filing_date": {
          "$date": "2018-01-03T06:00:00Z"
        },
        "instrument_type": {
          "code": "COM",
          "definition": "COMPLAINT"
        },
        "next_appearance_date": {
          "$date": "2018-01-05T06:00:00Z"
        },
        "rundate": {
          "$date": "2018-01-04T06:00:00Z"
        }
      }
    ]
  }
}
```

This endpoint retrieves criminal case filings.

### HTTP Request

`GET /v1/filings`

### Query Parameters

Filter query results by setting query parameters.

Parameter | Required | Type | Description | Valid Values
--------- | -------- | ---- | ----------- | ------------
rundate_min | optional | string | The earliest value to search for the report run date. | Date string in the format `YYYY-MM-DD`
rundate_max | optional | string | The latest value to search for the report run date. | Date string in the format `YYYY-MM-DD`
filing_date_min | optional | string | The earliest value to search for the filing date. | Date string in the format `YYYY-MM-DD`
filing_date_max | optional | string | The latest value to search for the filing date. | Date string in the format `YYYY-MM-DD`
instrument_type | optional | string | Initial charging document, motions to revoke, motions for new trial granted, and appeal documents | URL encoded text. Example: `motion%20new%20trial%20denied`. For a list of valid strings query the following endpoint: `GET /v1/fields/instrument_type`
case_disposition | optional | string | Final disposition of the case. | URL encoded text. Example: `not%20guilty`. For a list of valid strings query the following endpoint: `GET /v1/fields/case_disposition`
court_division_indicator | optional | string | Type of case or court | `felony` `misdemeanor`
case_status | optional | string | Case status | URL encoded text. Example: `dismissed`. For a list of valid strings query the following endpoint: `GET /v1/fields/case_status`
defendant_status | optional | string | Defendant status | URL encoded text. Example: `probation`. For a list of valid strings query the following endpoint: `GET /v1/fields/defendant_status`
bond_amount_min | optional | string | The minimum bond amount in US dollars. | Examples: `500` `1000`
bond_amount_max | optional | string | The maximum bond amount in US dollars. | Examples : `500` `1000`
current_offense | optional | string | The specific offense. | URL encoded text. Examples: `assault` `poss%20marijuana` `burglary`
next_appearance_date_min | optional | string | The earliest value to search for the next appearance date. | Date string in the format `YYYY-MM-DD`
next_appearance_date_max | optional | string | The latest value to search for the next appearance date. | Date string in the format `YYYY-MM-DD`
docket_calendar_name | optional | string | The calendar/queue which cases sit until ready for trial. | URL encoded text. Examples: `plea` `probable%20cause` `jury%20trial`. For a list of valid strings query the following endpoint: `GET /v1/fields/docket_calendar_name`
calendar_reason | optional | string | The reason for case setting. | URL encoded text. Examples: `motion%20hearing` `amended` `jury%20trial`. For a list of valid strings query the following endpoint: `GET /v1/fields/calendar_reason`
current_offense_level_degree | optional | string | The level and degree of the current offense | URL encoded text. Examples: `felony` `misdemeanor` `class%20a`. For a list of valid strings query the following endpoint: `GET /v1/fields/current_offense_level_degree`
defendant_spn | optional | string | The system person number for the defendant | Example: `2322561`
defendant_sex | optional | string | The defendant's sex | `M` `F`
defendant_race | optional | string | The defendant's race | `asian` `pacific%20islander` `black` `native%20american` `multiracial` `unknown` `white`.  For a list of valid strings query the following endpoint: `GET /v1/fields/defendant_race`
defendant_dob_min | optional | string | The earliest date of birth value to search for the defendant. | Date string in the format `YYYY-MM-DD`
defendant_dob_max | optional | string | The latest date of birth value to search for the defendant. | Date string in the format `YYYY-MM-DD`
defendant_street_number | optional | string | The street number of the house of building of the defendants recorded address. | URL encoded text.
defendant_street_name | optional | string | The street name of the defendants recorded address. | URL encoded text.
defendant_street_address | optional | string | The street address of the defendants recorded address. | URL encoded text.
defendant_street_city | optional | string | The city of the defendants recorded address. | URL encoded text.
defendant_state | optional | string | The state of the defendants recorded address. | URL encoded text.
defendant_zip_code | optional | string | The zip code of the defendants recorded address. | URL encoded text.
defendant_birthplace | optional | string | The birthplace of the defendant. | URL encoded text. For a list of valid strings query the following endpoint: `GET /v1/fields/defendant_birthplace`
defendant_uscitizen | optional | string | US citizenship filter for defendants. | URL encoded text. `Y` `N`
attorney_spn | optional | string | The system person number for the attorney | Example: `2533743`
attorney_connection | optional | string | The attorney's association with the case | URL encoded text. Examples: `hired%20defense` `appointed`
fields | optional | string | A comma separated list of fields the return in the results | `rundate` `filing_date` `instrument_type` `case_disposition` `court_division_indicator` `case_status` `defendant_status` `bond_amount` `current_offense` `next_appearance_date` `docket_calendar_name` `calendar_reason` `current_offense_level_degree` `defendant_spn` `defendant_sex` `defendant_race` `defendant_dob` `defendant_street_number` `defendant_street_name` `defendant_street_address` `defendant_city` `defendant_state` `defendant_zip_code` `defendant_birthplace` `defendant_uscitizen` `attorney_spn` `attorney_connection`
batch_size | optional | int | The size of each batch of results returned `default: 10000` | Any integer greater than `0`
limit | optional | int | The total number of results returned `default: 1000000` | Any integer greater than `0`
query | optional | string | A string use to request cached results or the next batch for a paginated query | A valid query identifier. Found in the json results `data.metadata.query` or `data.metadata.next`

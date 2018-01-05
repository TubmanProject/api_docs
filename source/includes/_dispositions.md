# Dispositions

Criminal case dispositions filed in county or district courts that have a future setting date. Use the Dispositions API calls to request disposition information.

## Get Dispositions

> Example Request:

```shell
curl -H "Content-Type:application/json" -X GET "http://tubmanproject-api.mintyross.com/v1/dispositions?rundate_min=2018-01-02&rundate_max=2018-01-23&defendant_race=black&current_offense_level_degree=felony"
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
          "href": "/v1/dispositions?query=L3YxL2Rpc3Bvc2l0aW9ucz9ydW5kYXRlX21pbj0yMDE4LTAxLTAyJnJ1bmRhdGVfbWF4PTIwMTgtMDEtMjMmZGVmZW5kYW50X3JhY2U9YmxhY2smY3VycmVudF9vZmZlbnNlX2xldmVsX2RlZ3JlZT1mZWxvbnk=_1"
        },
        "self": {
          "href": "/v1/dispositions?query=L3YxL2Rpc3Bvc2l0aW9ucz9ydW5kYXRlX21pbj0yMDE4LTAxLTAyJnJ1bmRhdGVfbWF4PTIwMTgtMDEtMjMmZGVmZW5kYW50X3JhY2U9YmxhY2smY3VycmVudF9vZmZlbnNlX2xldmVsX2RlZ3JlZT1mZWxvbnk=_1"
        }
      },
      "next": "L3YxL2Rpc3Bvc2l0aW9ucz9ydW5kYXRlX21pbj0yMDE4LTAxLTAyJnJ1bmRhdGVfbWF4PTIwMTgtMDEtMjMmZGVmZW5kYW50X3JhY2U9YmxhY2smY3VycmVudF9vZmZlbnNlX2xldmVsX2RlZ3JlZT1mZWxvbnk=_1",
      "query": "L3YxL2Rpc3Bvc2l0aW9ucz9ydW5kYXRlX21pbj0yMDE4LTAxLTAyJnJ1bmRhdGVfbWF4PTIwMTgtMDEtMjMmZGVmZW5kYW50X3JhY2U9YmxhY2smY3VycmVudF9vZmZlbnNlX2xldmVsX2RlZ3JlZT1mZWxvbnk=_1",
      "total": 67
    },
    "results": [
      {
        "attorney": {
          "connection": {
            "code": "AAT",
            "definition": "APPOINTED DEFENSE ATTORNEY"
          },
          "name": "JANIK, PAGE E.",
          "spn": "60570100"
        },
        "bond_amount": 2500,
        "calendar_reason": {
          "code": "PACA",
          "definition": "PRELIMINARY ASSIGNED COURT APPEARANCE"
        },
        "case_disposition": {
          "code": "DADJ",
          "definition": "DEFERRED ADJUDICATION OF GUILT"
        },
        "case_number": "157534801010",
        "case_status": {
          "code": "R",
          "definition": "PENDING COMPLETION OF PROBATION"
        },
        "complainant": {
          "agency": "HOUSTON POLICE DEPARTMENT",
          "name": "ALOBAIDI, A A"
        },
        "court": "179",
        "court_division_indicator": {
          "code": "003",
          "definition": "felony"
        },
        "current_offense": {
          "code": "131408",
          "definition": "ASLT FAM/HOUSE MEM IMPED BRTH/",
          "level_degree": {
            "code": "F3",
            "definition": "FELONY THIRD DEGREE"
          }
        },
        "defendant": {
          "address": {
            "city": "HOUSTON",
            "state": "TX",
            "street_address": "14222 KIMBERLEY LN",
            "street_name": "KIMBERLEY LN",
            "street_number": "14222",
            "zip_code": "77079"
          },
          "date_of_birth": {
            "$date": "1993-03-29T06:00:00Z"
          },
          "name": "CASTILLO, ALEJANDRO",
          "race": {
            "code": "W",
            "definition": "WHITE"
          },
          "sex": "M",
          "spn": "02930670"
        },
        "defendant_status": {
          "code": "A",
          "definition": "DEFERRED ADJUDICATION OF GUILT"
        },
        "disposition": "DEFERRED ADJUD OF GUILT",
        "disposition_date": {
          "$date": "2018-01-02T06:00:00Z"
        },
        "docket_calendar_name": {
          "code": "AC",
          "definition": "ASSIGNED COURT"
        },
        "filing_date": {
          "$date": "2017-12-29T06:00:00Z"
        },
        "instrument_type": {
          "code": "FIN",
          "definition": "FELONY INFORMATION"
        },
        "next_appearance_date": {
          "$date": "2018-01-02T06:00:00Z"
        },
        "offense_report_number": "162892317",
        "rundate": {
          "$date": "2018-01-04T06:00:00Z"
        },
        "sentence": "3 YEARS PROBATION, $600 FINE"
      }
    ]
  }
}
```

This endpoint retrieves criminal case dispositions.

### HTTP Request

`GET /v1/dispositions`

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
attorney_spn | optional | string | The system person number for the attorney | Example: `2533743`
attorney_connection | optional | string | The attorney's association with the case | URL encoded text. Examples: `hired%20defense` `appointed`
disposition_date_min | optional | string | The earliest value to search for the date of case disposition | Date string in the format `YYYY-MM-DD`
disposition_date_max | optional | string | The earliest value to search for the date of case disposition | Date string in the format `YYYY-MM-DD`
disposition | optional | string | The type of case disposition | URL encoded text. Examples: `dismissed` `conviction` `deferred`
sentence | optional | string | The defendants sentence | URL encoded text. Examples: `10%20days` `adjudication` `termination`
complainant_name | optional | string | The name of the complainant | URL encoded text.
complainant_agency | optional | string | The agency the complainant belongs to. | URL encoded text.
offense_report_number | optional | string | The offense report number | URL encoded text. Examples `HC170081858`, `1704030`
fields | optional | string | A comma separated list of fields the return in the results | `rundate` `filing_date` `instrument_type` `case_disposition` `court_division_indicator` `case_status` `defendant_status` `bond_amount` `current_offense` `next_appearance_date` `docket_calendar_name` `calendar_reason` `current_offense_level_degree` `defendant_spn` `defendant_sex` `defendant_race` `defendant_dob` `defendant_street_number` `defendant_street_name` `defendant_street_address` `defendant_city` `defendant_state` `defendant_zip_code` `attorney_spn` `attorney_connection` `disposition_date` `disposition` `sentence` `complainant_name` `complainant_agency` `offense_report_number`
batch_size | optional | int | The size of each batch of results returned `default: 10000` | Any integer greater than `0`
limit | optional | int | The total number of results returned `default: 1000000` | Any integer greater than `0`
query | optional | string | A string use to request cached results or the next batch for a paginated query | A valid query identifier. Found in the json results `data.metadata.query` or `data.metadata.next`

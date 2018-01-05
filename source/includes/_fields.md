# Fields

List the values for fields related to filings and dispositions.

## Get Fields

> Example Request:

```shell
curl -H "Content-Type:application/json" -X GET "http://tubmanproject-api.mintyross.com/v1/fields/defendant_status"
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
          "href": "/v1/fields/defendant_status?query=L3YxL2ZpZWxkcy9kZWZlbmRhbnRfc3RhdHVzPw==_1"
        },
        "self": {
          "href": "/v1/fields/defendant_status?query=L3YxL2ZpZWxkcy9kZWZlbmRhbnRfc3RhdHVzPw==_1"
        }
      },
      "next": "L3YxL2ZpZWxkcy9kZWZlbmRhbnRfc3RhdHVzPw==_1",
      "query": "L3YxL2ZpZWxkcy9kZWZlbmRhbnRfc3RhdHVzPw==_1",
      "total": 26
    },
    "results": [
      {
        "code": "A",
        "definition": "DEFERRED ADJUDICATION OF GUILT"
      },
      {
        "code": "B",
        "definition": "BOND MADE"
      },
      {
        "code": "C",
        "definition": "CITY JAIL  (FOR HOUSTON JAIL ONLY)"
      }
    ]
  }
}
```

This endpoint retrieves defendant birthplace fields.

### HTTP Request

`GET /v1/fields/{field}`

### Path Parameters

Get valid values for criminal disposition and filing fields.

Parameter | Required | Type | Description | Valid Values
--------- | -------- | ---- | ----------- | ------------
{field} | required | string | Name of a searchable criminal disposition or filing field | `court_division_indicator` `instrument_type` `case_disposition` `case_status` `defendant_status` `current_offense_level_degree` `docket_calendar_name` `calendar_reason` `defendant_race` `defendant_birthplace` `defendant_birthplace`

### Query Parameters

Filter query results by setting query parameters.

Parameter | Required | Type | Description | Valid Values
--------- | -------- | ---- | ----------- | ------------
batch_size | optional | int | The size of each batch of results returned `default: 10000` | Any integer greater than `0`
limit | optional | int | The total number of results returned `default: 1000000` | Any integer greater than `0`
query | optional | string | A string use to request cached results or the next batch for a paginated query | A valid query identifier. Found in the json results `data.metadata.query` or `data.metadata.next`

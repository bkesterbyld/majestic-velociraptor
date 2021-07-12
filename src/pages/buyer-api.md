---
seo:
  title: ''
  description: ''
  robots: []
  extra: []
  type: stackbit_page_meta
template: page
---
## Sitewire Property API (Colchis)

Stability: production; for discussion and in development for Colchis

List of Property Data API fields below. Note that we have other fields in separate APIs you might want to access such as:

*   Borrower Name (Company Name)

*   Percentage completion of both property and individual items (based on approval amounts/budget)

*   Start and end dates for the loan (entered by Lender)

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **borrower_id** | *integer* | unique identifier of the borrower | 1234 |
| **budget:allow_new_draw** | *boolean* | Indicate whether new draw can be created. This is false when there are drafting draws. | true |
| **budget:id** | *integer* | unique identifier of the budget | 1234 |
| **csz** | *string* | The city, state and zip. | "New York, NY 10007" |
| **draws** | *array* | List of draws for this property | \[{"id":1234,"name":"Draw 1","borrower_view_status":"Wire initiated","aasm_state":"pending","allow_overage":true,"total_budget_cents":600000,"total_available_cents":400000,"total_requested_cents":200000,"total_released_cents":160000,"total_approved_cents":200000,"overage_cents":1000,"percentage_requested":15.0,"percentage_released":15.0,"lender_budget":80,"has_inspection_image":true,"requests":\[{"id":1234,"name":"Windows","budgeted_cents":200000,"available_cents":100000,"requested_cents":200000,"approved_cents":200000,"released_cents":160000,"total_requested_cents":200000,"total_approved_cents":200000,"total_released_cents":160000,"allow_overage":true,"required_image_count":3,"required_video_count":1,"street":"123 Main St","csz":"New York, NY 10007"}]}] |
| **full_address** | *string* | Full address with unit | "101 Main St #2, New York, NY 10007" |
| **id** | *integer* | unique identifier of property | 1234 |
| **job_items/budget_id** | *integer* | unique identifier of the budget | 1234 |
| **job_items/budgeted_cents** | *integer* | Budget for all draws | 200000 |
| **job_items/budgeted_currency** | *string* | Currency for budgeted_cents | "USD" |
| **job_items/created_at** | *date-time* | when job item was created | "2015-01-01T12:00:00Z" |
| **job_items/id** | *integer* | unique identifier of the job item | 1234 |
| **job_items/name** | *string* | Name of job item | "Windows" |
| **job_items/updated_at** | *date-time* | when job item was updated | "2015-01-01T12:00:00Z" |
| **lender_budget** | *nullable integer* | Percentage of budget the lender pays. When null, it means this lender always pays 100%. | 80 |
| **lender_email** | *string* | Lender primary email | "name@example.com" |
| **lender_id** | *integer* | unique identifier of the lender | 1234 |
| **loan_number** | *string* | Loan number | "201-555" |
| **lockbox_code** | *string* | Code for lockbox on property | "12345" |
| **overage_cents** | *integer* | Amount over the budget | 100000 |
| **street** | *string* | The street address. | "101 Main St" |
| **summary_url** | *string* | Tokenized URL for direct sign in to web app to show the borrower property summary report. | "https://app.sitewire.co/borrower/properties/summary?token=eyJfcmF" |
| **total_approved_cents** | *integer* | Total approved across all approved draws. | 3000000 |
| **total_available_cents** | *integer* | Total approved across all approved draws. | 3000000 |
| **total_budget_cents** | *integer* | Total budget for the property. | 6000000 |
| **total_released_cents** | *integer* | Total released across all completed draws. | 2400000 |
| **total_requested_cents** | *integer* | Total requested across all draws. | 3000000 |





### Properties Info



Info for existing property.

    GET /api/v1/properties/{property_id}

#### Curl Example

    $ curl -n https://app.sitewire.co/api/v1/properties/$PROPERTY_ID

#### Response Example

    HTTP/1.1 200 OK

<!---->

    {
      "id": 1234,
      "lender_id": 1234,
      "borrower_id": 1234,
      "loan_number": "201-555",
      "lockbox_code": "12345",
      "full_address": "101 Main St #2, New York, NY 10007",
      "street": "101 Main St",
      "csz": "New York, NY 10007",
      "total_budget_cents": 6000000,
      "total_available_cents": 3000000,
      "total_requested_cents": 3000000,
      "total_approved_cents": 3000000,
      "total_released_cents": 2400000,
      "overage_cents": 100000,
      "lender_email": "name@example.com",
      "lender_budget": 80,
      "summary_url": "https://app.sitewire.co/borrower/properties/summary?token=eyJfcmF",
      "draws": [
        {
          "id": 1234,
          "name": "Draw 1",
          "borrower_view_status": "Wire initiated",
          "aasm_state": "pending",
          "allow_overage": true,
          "total_budget_cents": 600000,
          "total_available_cents": 400000,
          "total_requested_cents": 200000,
          "total_released_cents": 160000,
          "total_approved_cents": 200000,
          "overage_cents": 1000,
          "percentage_requested": 15.0,
          "percentage_released": 15.0,
          "lender_budget": 80,
          "has_inspection_image": true,
          "requests": [
            {
              "id": 1234,
              "name": "Windows",
              "budgeted_cents": 200000,
              "available_cents": 100000,
              "requested_cents": 200000,
              "approved_cents": 200000,
              "released_cents": 160000,
              "total_requested_cents": 200000,
              "total_approved_cents": 200000,
              "total_released_cents": 160000,
              "allow_overage": true,
              "required_image_count": 3,
              "required_video_count": 1,
              "street": "123 Main St",
              "csz": "New York, NY 10007"
            }
          ]
        }
      ],
      "budget": {
        "id": 1234,
        "allow_new_draw": true
      },
      "job_items": [
        {
          "id": 1234,
          "name": "Windows",
          "budgeted_cents": 200000,
          "budgeted_currency": "USD",
          "created_at": "2015-01-01T12:00:00Z",
          "updated_at": "2015-01-01T12:00:00Z",
          "budget_id": 1234
        }
      ]
    }





### Properties List



List existing properties.

    GET /api/v1/properties

#### Curl Example

    $ curl -n https://app.sitewire.co/api/v1/properties

#### Response Example

    HTTP/1.1 200 OK

<!---->

    [
      {
        "id": 1234,
        "lender_id": 1234,
        "borrower_id": 1234,
        "loan_number": "201-555",
        "lockbox_code": "12345",
        "full_address": "101 Main St #2, New York, NY 10007",
        "street": "101 Main St",
        "csz": "New York, NY 10007",
        "total_budget_cents": 6000000,
        "total_requested_cents": 3000000,
        "total_approved_cents": 3000000,
        "total_available_cents": 3000000,
        "total_released_cents": 2400000,
        "overage_cents": 100000,
        "lender_email": "name@example.com",
        "lender_budget": 80,
        "summary_url": "https://app.sitewire.co/borrower/properties/summary?token=eyJfcmF",
        "draws": [
          {
            "id": 1234,
            "name": "Draw 1",
            "borrower_view_status": "Wire initiated",
            "aasm_state": "pending",
            "allow_overage": true,
            "total_budget_cents": 600000,
            "total_available_cents": 400000,
            "total_requested_cents": 200000,
            "total_released_cents": 160000,
            "total_approved_cents": 200000,
            "overage_cents": 1000,
            "percentage_requested": 15.0,
            "percentage_released": 15.0,
            "lender_budget": 80,
            "has_inspection_image": true,
            "requests": [
              {
                "id": 1234,
                "name": "Windows",
                "budgeted_cents": 200000,
                "available_cents": 100000,
                "requested_cents": 200000,
                "approved_cents": 200000,
                "released_cents": 160000,
                "total_requested_cents": 200000,
                "total_approved_cents": 200000,
                "total_released_cents": 160000,
                "allow_overage": true,
                "required_image_count": 3,
                "required_video_count": 1,
                "street": "123 Main St",
                "csz": "New York, NY 10007"
              }
            ]
          }
        ],
        "budget": {
          "id": 1234,
          "allow_new_draw": true
        }
      }
    ]


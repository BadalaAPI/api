# Payin Outlets

Payin outlets are establishments where users can send cash to convert to
Bitcoins. Payment received from these outlets will be processed by coins.ph,
or coins.co.th, depending on the outlet's region. This API allows users to get
payin outlet data, which includes their categories, and a table of fees.

## Getting Payin Outlets

This endpoint returns payin outlets, with their types. A payin outlet has the
following properties:

* **id** - A unique identifier for the payin outlet
* **payment_outlet_type** - The outlet's category. These are usually establishments where coins accepts fiat.
* **name** - The outlet's name in human readable form.
* **region** - An [ISO 3166-1 Alpha 2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code of the region where the outlet is located.
* **help_text** - Optional text that further describes the outlet. May be null.
* **help_link** - Optional help article that further describes the outlet. May be null.
* **instructions** - Instructions on how the user should process payment through the outlet.

### HTTP Method

**GET**

### Endpoint

https://coins.ph/d/api/payin-outlets/

### Example Response

```json
{
    "payin-outlets": [
        {
            "id": "citibank_deposit",
            "payment_outlet_type": {
                "id": "bank_deposit",
                "name": "Bank Deposit",
                "fields": [],
                "fee_structure_description": null,
                "payout_duration_description": null
            },
            "name": "Citibank",
            "region": "PH",
            "help_text": "",
            "help_link": "",
            "instructions": "Deposit to account 1234"
        },
        {
            "id": "bdo_deposit",
            "payment_outlet_type": {
                "id": "bank_deposit",
                "name": "Bank Deposit",
                "fields": [],
                "fee_structure_description": null,
                "payout_duration_description": null
            },
            "name": "BDO Bank",
            "region": "PH",
            "help_text": "",
            "help_link": "",
            "instructions": "Deposit to account 5169"
        }
    ],
    "meta": {
        "total_count": 6,
        "next_page": null,
        "previous_page": null
    }
}
```

## Payin Outlet Categories

Payin outlets are grouped into categories. Unlike
[Payout Outlet Categories](payout-outlets-api.md), payin outlet categories
usually don't have required fields. Payin outlet categories have the following
properties:

* **id** - Unique identifier for the payout outlet category.
* **name** - The category's name in human readable form.
* **fields** - A collection of fields that payment outlets of this category requires.
* **fee_structure_description** - Describes how fees in this category are structured in general.
* **payout_duration_description** - Describes how long it usually takes to process BTC payouts to outlets of this category.

### HTTP Method

**GET**

### Endpoint

https://coins.ph/d/api/payin-outlet-categories/

### Example Response

```json
{
    "payin-outlet-categories": [
        {
            "id": "bank_deposit",
            "name": "Bank Deposit",
            "fields": [],
            "fee_structure_description": null,
            "payout_duration_description": null
        },
        {
            "id": "validated_deposit",
            "name": "Validated Bank Deposit",
            "fields": [],
            "fee_structure_description": null,
            "payout_duration_description": null
        }
    ],
    "meta": {
        "total_count": 3,
        "next_page": null,
        "previous_page": null
    }
}
```

## Payin Outlet Fees

### HTTP Method

**GET**

### Endpoint

https://coins.ph/d/api/payin-outlet-fees/

### Example Response

```json
{
    "payin-outlet-fees": [
        {
            "payment_outlet": "bdo_deposit",
            "currency": "PHP",
            "from_amount": "0",
            "until_amount": "100000000",
            "fee_amount": "0",
            "fee_percent": "0.01"
        },
        {
            "payment_outlet": "bpi_deposit",
            "currency": "PHP",
            "from_amount": "0",
            "until_amount": "100000",
            "fee_amount": "100",
            "fee_percent": "0"
        }
    ],
    "meta": {
        "total_count": 6,
        "next_page": null,
        "previous_page": null
    }
}
```
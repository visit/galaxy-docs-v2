# Example Workflow

> Example Workflow

This section will provide a very basic example workflow for booking a hotel room for one adult and one child that encompasses creating a basket, searching for availability, adding items and customer information, commiting then checking the reservation and, finally,  cancelling it. For each step, see to the right of the page for ptototype calls using cURL or simple Javascript calls as well as example responses. Each of these calls (not counting the API keys and specific parameters that you will need to plug in) are the minimum requirements for a successful response.

Choose a Point of Sale
Choose a currency
Search availability
Create basket
Add booking item
Add customer info
Commit Basket
Get Status
Review reservation
Cancel Reservation

## Get Point of Sale

```shell
curl -X GET 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/pointofsales'

```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/pointofsales",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
	 "Accept-Language": "en-US"
  }  
});
```

> Response:

```json
[
  {
    "Id": 1234561,
    "Name": "Online"
  },
  {
    "Id": 1234562,
    "Name": "online viktors hotell 3"
  },
  {
    "Id": 1234565,
    "Name": "callcenter test"
  },
  {
    "Id": 1234569,
    "Name": "Veras Call Center"
  },
  {
    "Id": 1234570,
    "Name": "Test salespoint Distribution API"
  }
]
```
The first step is to obtain a valid <a href="https://visit.github.io/galaxy-docs-v2/#point-of-sales">Point of Sale</a> Identifier. This is needed for many of the following operations and defines the products available for search as well as many of the settings important for creating a booking, such as rate codes availability periods, etc. We will go with the "Test salespoint Distribution API" Point of Sale - **1234570**

### HTTP Request

`GET https://galaxy.citybreak.com/v2/api/pointofsales`



## Choose A Currency 

```shell
curl -X GET 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/pointofsales/currencies/1234570'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/pointofsales/currencies/1234570",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
   "Accept-Language": "en-US"
  }  
});
```

> Example of response:

```json
[
  "DKK",
  "SEK",
  "NOK",
  "EUR"
]
```

Once we have a Point of Sale we need to choose a <a href="https://visit.github.io/galaxy-docs-v2/#currencies">Currency</a>. Rates for hotel room products in the <a href="https://visit.github.io/galaxy-docs-v2/#currencies">Availability Search</a> are shown in whatever currency you choose but certain hotels do not have products for sale in all currencies so your results may be filtered depending on the currency you choose. We will choose Swedish Kronor - **SEK**.

### HTTP Request

`GET https://galaxy.citybreak.com/v2/api/pointofsales/currencies/1234570`





## Create A Basket

```shell
curl -X POST 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 'https://galaxy.citybreak.com/v2/api/basket/create/1234570/SEK'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/basket/create/1234570/SEK",
{
  method:"POST"
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }
});
```

> Example of response:

```json
{
  "BasketId": 87654321,
  "Success": true
}
```

For all booking operations you will need a <a href="https://visit.github.io/galaxy-docs-v2/#create-basket">Shopping Basket</a>. This entity will be the reference for all information related to a booking, right up until the time the customer decides to commit to the booking and has provided all the necessary information. It is therefore very important to hold a reference to the BasketId, in this case - **87654321**

### HTTP Request

`POST https://galaxy.citybreak.com/v2/api/basket/create`





## Search Availability

```shell
curl -X POST 
--header 'Content-Type: application/json' 
--header 'Accept: application/json' 
--header 'Accept-Language: en-us' 
--header 'apiKey: APIKEY132456789EWOK' -d '{
   "PointOfSalesId": 1234570,
   "Arrival": "2017-10-14T12:27:58.851Z",
   "Departure": "2017-10-15T12:27:58.851Z",
   "Currency": "SEK",
   "PageSize": 20,
   "Page": 0,
   "PersonConfigurations": [
     {
       "Adults": 1,
       "ChildrenAges": [
         1
       ] 
     }
   ]
 }' 'https://galaxy.citybreak.com/v2/api/availability/accommodation'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/availability/accommodation",
{
	method: "POST",
	headers: {
	    "ApiKey:" "APIKEY132456789EWOK",
	    "Accept": "application/json",
		 "Accept-Language": "en-US"
	},
	body: JSON.Stringify({
	   "PointOfSalesId": 1234570,
	   "Arrival": "2017-10-14T12:27:58.851Z",
	   "Departure": "2017-10-15T12:27:58.851Z",
	   "Currency": "SEK",
	   "PageSize": 20,
	   "Page": 0,
	   "PersonConfigurations": [
	     {
	       "Adults": 1,
	       "ChildrenAges": [
	         1
	       ] 
	     }
	   ]
	})  
});
```

> Example of response:

```json
{
  "AccommodationSearch": {
    "PointOfSalesId": 1234570,
    "Arrival": "2017-10-14T00:00:00Z",
    "Departure": "2017-10-15T00:00:00Z",
    "Currency": "SEK",
    "PageSize": 20,
    "Page": 0,
    "Sort": {
      "Order": 0,
      "Field": "Price"
    },
    "PersonConfigurations": [
      {
        "Adults": 1,
        "ChildrenAges": [
          1
        ]
      }
    ],
    "ContentFilter": null,
    "OutputFilter": null
  },
  "Accommodations": [
    {
      "Id": 1136433,
      "Name": "Edelbrock Hotell 3",
      "Content": {
        "PriceFrom": 0,
        "Images": [
          {
            "Uri": "//images.citybreak.com/image.aspx?ImageId=4014876",
            "IsMain": true,
            "Name": null,
            "Copyright": null,
            "Description": null
          },
          {
            "Uri": "//images.citybreak.com/image.aspx?ImageId=4014877",
            "IsMain": false,
            "Name": null,
            "Copyright": null,
            "Description": null
          }
        ],
        "Information": [
          {
            "Id": 99,
            "Name": "Name",
            "Value": "Edelbrock Hotell 3"
          },
          {
            "Id": 101,
            "Name": "Introduction",
            "Value": "Edelbrock Hotell"
          },
          {
            "Id": 102,
            "Name": "Description",
            "Value": "Edelbrock Hotell!"
          },
          {
            "Id": 100038,
            "Name": "Elevator",
            "Value": "False"
          },
          {
            "Id": 100163,
            "Name": "Reception",
            "Value": "False"
          }
        ],
        "Categories": null,
        "Geos": [],
        "Pois": [],
        "Position": null
      },
      "Placements": [
        {
          "Price": {
            "Price": 450,
            "TotalPersons": 2,
            "Currency": "SEK",
            "DateStart": "2017-10-14T00:00:00Z",
            "DateEnd": "2017-10-15T00:00:00Z"
          },
          "Placements": [
            {
              "Name": "Dubbelrum med xbädd ÖSD",
              "Content": {
                "PriceFrom": null,
                "Images": [],
                "Information": [
                  {
                    "Id": 99,
                    "Name": "Name",
                    "Value": "Dubbelrum med xbädd ÖSD"
                  }
                ],
                "Categories": null,
                "Geos": null,
                "Pois": null,
                "Position": null
              },
              "IncludedSubProducts": [],
              "MaxPopopulation": 3,
              "MinPopulation": 1,
              "ExtraBeds": 1,
              "PersonConfiguration": {
                "Adults": 1,
                "ChildrenAges": [
                  1
                ]
              },
              "PricePeriods": [
                {
                  "DateStart": "2017-10-14T00:00:00",
                  "DateEnd": "2017-10-15T00:00:00",
                  "AdultPrice": 300,
                  "ChildPrice": 150,
                  "TotalPrice": 450,
                  "Currency": "SEK"
                }
              ],
              "BookingConditions": {
                "Name": null,
                "Terms": null
              }
            }
          ],
          "BookingKey": "18-A"
        },
        {
          "Price": {
            "Price": 500,
            "TotalPersons": 2,
            "Currency": "SEK",
            "DateStart": "2017-10-14T00:00:00Z",
            "DateEnd": "2017-10-15T00:00:00Z"
          },
          "Placements": [
            {
              "Name": "Dubbelrum ÖSD",
              "Content": {
                "PriceFrom": null,
                "Images": [],
                "Information": [
                  {
                    "Id": 99,
                    "Name": "Name",
                    "Value": "Dubbelrum ÖSD"
                  }
                ],
                "Categories": null,
                "Geos": null,
                "Pois": null,
                "Position": null
              },
              "IncludedSubProducts": [
                {
                  "Name": "Trädgårdstomte",
                  "Content": {
                    "PriceFrom": null,
                    "Images": [],
                    "Information": [
                      {
                        "Id": 99,
                        "Name": "Name",
                        "Value": "Trädgårdstomte"
                      }
                    ],
                    "Categories": null,
                    "Geos": null,
                    "Pois": null,
                    "Position": null
                  },
                  "Price": 150,
                  "Amount": 1,
                  "Currency": "SEK",
                  "PriceIncluded": false,
                  "IsExtraBed": false,
                  "PayOnSite": false
                }
              ],
              "MaxPopopulation": 3,
              "MinPopulation": 1,
              "ExtraBeds": 1,
              "PersonConfiguration": {
                "Adults": 1,
                "ChildrenAges": [
                  1
                ]
              },
              "PricePeriods": [
                {
                  "DateStart": "2017-10-14T00:00:00",
                  "DateEnd": "2017-10-15T00:00:00",
                  "AdultPrice": 250,
                  "ChildPrice": 100,
                  "TotalPrice": 350,
                  "Currency": "SEK"
                }
              ],
              "BookingConditions": {
                "Name": null,
                "Terms": null
              }
            }
          ],
          "BookingKey": "19-A"
        }
      ],
      "TotalResults": 2
    }
  ],
  "SearchId": "899fe054-3bb4-4ff8-b577-ba716b0b3317",
  "ExpirationDate": "2017-09-15T09:15:46.0619347Z",
  "TotalResults": 1
}
```

At a minimum, an <a href="https://visit.github.io/galaxy-docs-v2/#accommodation-15">Availability Search</a> requires the **PointOfSalesId** we obtained earlier (1234570) and the **Currency** ("SEK") as well as the **Arrival** and **Departure** dates we want to search for, the **PersonConfigurations** (i.e. the number of guests both Adult and Child), and the "PageSize" of the result you want. If there are 50 results and you want to have 20 products at a time, you can check the total number products in the first response at **Page** 0 and repeat the request incrementing the **Page** as necessary. 

The information above is one of the most complex and probably the most important parts of the Galaxy API. It returns a list of "Accommodations", which in this case for Citybreak are Hotel Properties (or Bed & Breakfasts, Apartments, etc), within which is a list of "Placements" which are Hotel Rooms (or Beds or Apartments, etc. depending on the property. These may also come with compulsory Add-ons (also known as sub-products) like breakfast included or champagne on arrival. 

Each Accomodation object will also have content information about the property, that can also be found in an <a href="https://visit.github.io/galaxy-docs-v2/#accommodation">Accommodation Search</a>, and how many room types (Placements) are available. 

The placement objects represent the products that will actually be booked. As such they have a lot of the important information a customer might want to see, they contain a "Price" that represents total spend as well as a "PricePeriods" list that breaks the cost dow for example. Other useful information might be included in the content info or the room configuration/occupancy allowances, etc. The most important information for the booking process however is the **BookingKey**. There is one per "Placement" and is used to <a href="https://visit.github.io/galaxy-docs-v2/#add-booking-item">add a product to a Basket</a>.

Also required is the **SearchId** that represents your search. The object represented by this unique id will hold references to all the products that were returned in the Accomodation Search. Also keep note of the **ExpirationDate** of the search as the reference will be invalid after this timestamp is passed.

For this example we will use the double room at Edelbrock Hotell 3 with a handy Garden Gnome included:

"BookingKey" = **19-A**
"SearchId" = **899fe054-3bb4-4ff8-b577-ba716b0b3317**

### HTTP Request

`POST https://galaxy.citybreak.com/v2/api/availability/accommodation`




## Add A Booking Item

```shell
curl -X PUT 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/basket/add/accommodation/87654321/899fe054-3bb4-4ff8-b577-ba716b0b3317/19-A'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/basket/add/accommodation/87654321/899fe054-3bb4-4ff8-b577-ba716b0b3317/19-A",
{
  method:"PUT"
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
  }  
});
```

> Example of response:

```json
true
```

Taking the **BasketId**: 87654321 of the basket we created earlier, the **SearchId**: 899fe054-3bb4-4ff8-b577-ba716b0b3317 from the availability search and the **BookingCode**: 19-A of the product we selected, we can now <a href="https://visit.github.io/galaxy-docs-v2/#add-booking-item">add a product to our Basket</a>.

`PUT https://galaxy.citybreak.com/v2/api/basket/add/accommodation/87654321/899fe054-3bb4-4ff8-b577-ba716b0b3317/19-A"`




## Add Customer Info


```shell
curl -X POST 
--header 'Content-Type: application/json' 
--header 'apiKey: APIKEY132456789EWOK' -d '{
   "NameFirst": "Test",
   "NameLast": "User",
   "Salutation": "Ms",
   "CustomerType": "Private",
   "Culture": "en-US",
   "Address": { 
     "StreetAddress1": "Test Road 123",
     "PostalCode": "41111",
     "City": "Gothenburg",
     "CountryCode": "SE"
   },
   "Email": "testuser%40visit.com",
   "PhoneMobile": { 
     "CountryCode": "46",
     "AreaCode": "07",
     "Number": "2222222"
   }
 }' 'https://galaxy.citybreak.com/v2/api/basket/customer/87654321'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/basket/customer/87654321",
{
  method:"POST"
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
  }  
  body: JSON.Stringify({
    "NameFirst": "Test",
    "NameLast": "User",
    "Salutation": "Ms",
    "CustomerType": "Private",
    "Culture": "en-US",
    "Address": {
      "StreetAddress1": "Test Road 123",
      "PostalCode": "41111",
      "City": "Gothenburg",
      "CountryCode": "SE"
    },
    "Email": "testuser@visit.com",
    "PhoneMobile": {
      "CountryCode": "46",
      "AreaCode": "07",
      "Number": "2222222"
    }
  }
}
});
```

> Example of response: no content

To commit a Basket we will need to <a href="https://visit.github.io/galaxy-docs-v2/#update-customer-information">provide Customer Information</a> using our **BasketId**: 87654321. In the example, we have created Ms. Test User and will POST her data which will attach it to the basket. You will only receive a status code of 204 to indicate success. The basket now has the bare minimum required to commit it.

### HTTP Request

`GET https://galaxy.citybreak.com/v2/api/basket/customer/87654321"`





## Commit Basket


```shell
curl -X POST 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/basket/commit/87654321'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/basket/commit/87654321",
{
  method:"POST"
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json",
  }  
});
```

> Example of response: an integer representing the CommitJobId

```json
98761234
```

Once you have all the information in the basket, you can <a href="https://visit.github.io/galaxy-docs-v2/#commit-basket">Commit</a> it. 
This will start the process of finalising bookings and generating the necessary financial information. 
You only need to provide the Basket Id for this call. 
The whole commit process is a two step one. 
First, in this call, we will use a POST call and the **BasketId**: 87654321 to trigger the Basket commit job. 
What you get in return is the **CommitJobId**, you should use it with <a href="https://visit.github.io/galaxy-docs-v2/#commit-status">Commit Status</a> to get the status of the job. 
Our CommitJobId is **98761234**.


### HTTP Request

`POST https://galaxy.citybreak.com/v2/api/basket/commit/87654321`







## Get Commit Job Status

```shell
curl -X GET 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/basket/commit/status/98761234'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/basket/commit/status/98761234",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "Status": "CompletedOk",
  "Subtasks": [
    {
      "Task": "StartingCommit",
      "Status": "CompletedOk",
      "ExtraInfo": null
    },
    {
      "Task": "CreatingConfirmations",
      "Status": "CompletedOk",
      "ExtraInfo": null
    },
    {
      "Task": "CreditCardAction",
      "Status": "CompletedOk",
      "ExtraInfo": null
    },
    {
      "Task": "CreatingInvoices",
      "Status": "NotStarted",
      "ExtraInfo": null
    },
    {
      "Task": "CreatingStatistics",
      "Status": "NotStarted",
      "ExtraInfo": null
    },
    {
      "Task": "FinishingTransaction",
      "Status": "CompletedOk",
      "ExtraInfo": null
    }
  ],
  "ResvVersionId": 12349876,
  "BookingCode": "EWOK12"
}
```

Once the basket has been ordered to be <a href="https://visit.github.io/galaxy-docs-v2/#commit-basket">Committed</a>, 
in order to get information about the booking you will need to use the **CommitJobId**: 98761234 to query the <a href="https://visit.github.io/galaxy-docs-v2/#commit-status">Commit Status</a> of the job. 
As you can see in the example return, there are a number of different tasks that run as a part of a commit job. 
All of these are running in the back ground. Continue polling /basket/commit/status/{id} until you get either CompletedOk ok Failed as status. 
Both of them are final statuses. If you get Ok your reservation is confirmed and you have the booking code in the result. 
If you get Fail you will be provided with some detailes what went wrong. Like if you failed to confirm the reservation in a sub system or you havent provided enough information.

The other important information returned by the status is the ResvVersionId (reservation version id), for us: **12349876** and the BookingCode, for us: **EWOK12**, which are used to obtain information about the <a href="https://visit.github.io/galaxy-docs-v2/#reservation">Reservation</a>

### HTTP Request

`GET https://galaxy.citybreak.com/v2/api/basket/commit/status/98761234`





## Review A Reservation


```shell
curl -X GET 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/reservation/latest/EWOK12'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/reservation/latest/EWOK12",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "BookingCode": "EWOK12",
  "Version": 1,
  "BookingDate": "2017-09-27T13:12:54.1938577Z",
  "AutoCancellation": "9999-12-31T23:59:59.9999999",
  "Fees": [],
  "BookingUser": {
    "Id": 113685,
    "NameFirst": "Galaxy",
    "NameLast": "Api user",
    "Email": null
  },
  "CancellationMessage": null,
  "Customer": {
    "NameFirst": "Test",
    "NameLast": "User",
    "Salutation": Ms,
    "CustomerNumber": null,
    "CustomerType": 0,
    "Culture": null,
    "CivicRegistrationNumber": null,
    "Company": null,
    "CompanyDepartment": null,
    "Address": {
      "StreetAddress1": "Test Road 123",
      "StreetAddress2": null,
      "StreetAddress3": null,
      "PostalCode": "41111",
      "City": "Gothenburg",
      "CountryCode": "SE",
      "State": null
    },
    "Email": null,
    "PhoneHome": {
      "CountryCode": null,
      "AreaCode": null,
      "Number": null
    },
    "PhoneWork": {
      "CountryCode": null,
      "AreaCode": null,
      "Number": null
    },
    "PhoneMobile": {
      "CountryCode": "46",
      "AreaCode": "07",
      "Number": "2222222"
    }
  },
  "ProductGroups": [
    {
      "Products": [
        {
          "Id": 3,
          "Name": "Dubbelrum ÖSD",
          "Price": 350
        }
      ],
      "Id": 153663,
      "Name": "Edelbrock Hotell"
    }
  ]
}
```

There are two ways to return information about a reservation, either by <a href="https://visit.github.io/galaxy-docs-v2/#get-reservation-version">the Version</a> of the Reservation, using the **BookingCode** and **ResVersionId** or by the latest version as we have done here where we just require our **BookingCode**: EWOK12. It displays limited information about the booked products, the customer and some meta information about the booking itself. The user should retain a reference to the **BookingCode** so that they are able to reference their reservation


### HTTP Request

`GET https://galaxy.citybreak.com/v2/api/reservation/latest/EWOK12`






## Cancel A Reservation


```shell
curl -X GET 
--header 'Accept: application/json' 
--header 'apiKey: APIKEY132456789EWOK' 
'https://galaxy.citybreak.com/v2/api/reservation/cancel/info/EWOK12'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/reservation/cancel/info/EWOK12",
{
  headers: {
    "ApiKey:" "APIKEY132456789EWOK",
    "Accept": "application/json"
  }  
});
```

> Example of response:

```json
{
  "BookingCode": "EWOK12",
  "NoProducts": 1,
  "ReservationVersionId": 12349876,
  "LastCancellationDate": "9999-12-31T23:59:59.9999999"
}
```

Finally, lets cancel our reservation. <a href="https://visit.github.io/galaxy-docs-v2/#cancel-reservationn">Cancelling</a> policies can vary for products and so it is worth noting here that the only guaranteed cancellation that of the reservation. There might be part or full payments due depending on policies, cancellation insurance and other factors, that can differ product to product. To cancel, we once again just require our **BookingCode**: EWOK12 and with a GET query we will close out our reservation and end the example workflow. 


### HTTP Request

`GET https://galaxy.citybreak.com/v2/api/reservation/cancel/info/EWOK12`

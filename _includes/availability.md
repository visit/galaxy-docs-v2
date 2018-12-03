# Availability

> Availability


**Availability** calls provide information about the availability of accomodation products and (seperately) cabin products. These product types are split due to the nature of Cabin booking, typically set periods like Mon-Thurs, that produce different results for searches. Hotels, etc. return results based on the provided arrival and departure date. Cabins produce a "fuzzier" result, looking for matching periods for the requested dates within a margin of error. Both searches will return products with availability, including content, pricing groups with room information (Placements) and subproduct information (such as breakfasts or tickets to nearby attractions), as well as a Search ID with its Expiry. 

The **Search Id** can be used to retrieve prior, cached searches in a much shorter amount of time for both Accomodation Search and Cabin Scan if used before its Expiry. The object recalled by the search contains all the unfiltered information retrieved in the first search, so further or different filtering on content, etc. can be done in this call.

The **Search Id** and the **Booking Key** of each room product are used in the basket operations to add the product found to the <a href="https://visit.github.io/galaxy-docs-v2/#Basket">Basket</a> 

The Cabin Search has additional functionality - the **GET** calls - 

**GET** and **POST** operations 
<aside class="notice">NB: if using the Visit Test Organisation API Key you can use 17692 as the **{pointOfSalesId}**</aside>

## Accommodation

```shell
curl -X POST 
--header 'Content-Type: application/json' 
--header 'Accept: application/json' 
--header 'Accept-Language: en-us' 
--header 'apiKey: APIKEY132456789EWOK' -d '{
   "PointOfSalesId": {pointOfSalesId},
   "Arrival": "2017-10-14T12:27:58.851Z",
   "Departure": "2017-10-15T12:27:58.851Z",
   "Currency": "SEK",
   "PageSize": 20,
   "PersonConfigurations": [
     {
       "Adults": 1,
       "ChildrenAges": [
         0
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
	   "PointOfSalesId": {pointOfSalesId},
	   "Arrival": "2017-10-14T12:27:58.851Z",
	   "Departure": "2017-10-15T12:27:58.851Z",
	   "Currency": "SEK",
	   "PageSize": 20,
	   "PersonConfigurations": [
	     {
	       "Adults": 1,
	       "ChildrenAges": [
	         0
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
    "PointOfSalesId": {pointOfSaleId},
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
          0
        ]
      }
    ],
    "ContentFilter": null,
    "OutputFilter": null
  },
  "Accommodations": [
    {
      "Id": "cbis:1136433",
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
                  0
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
                  0
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

This is a **POST** request that requires a filter with some mandatory properties, such as arrival and depature dates. 
The filter can also include content filtering, such as only those hotels associated with a particular CBIS category or that have 24 hr reception. 
Content possibilities can be found in the <a href="https://visit.github.io/galaxy-docs-v2/#content">Content Section</a> You can see a bare minimum verison of this search in the examples.
The Most important return values in this response are the **SearchId** and the **BookingKey** used in the <a href="https://visit.github.io/galaxy-docs-v2/#basket">Basket</a>, also pay attention to the *ExpirationDate* of the SearchId

### HTTP Request

`POST https://galaxy.citybreak.com/availability/accommodation`

### Query Parameters

Parameter | Description
--------- | -----------
filter | the POST filter
Accept-Language | The language culture (e.g en-us)

## Get Previous Search

```shell
curl -X POST 
--header 'Content-Type: application/json' 
--header 'Accept: application/json' 
--header 'Accept-Language: en-us' 
--header 'apiKey: APIKEY132456789EWOK' -d '{
   "PointOfSalesId": {pointOfSalesId},
   "Arrival": "2017-10-14T12:27:58.851Z",
   "Departure": "2017-10-15T12:27:58.851Z",
   "Currency": "SEK",
   "PageSize": 20,
   "Page": 1,
   "PersonConfigurations": [
     {
       "Adults": 1,
       "ChildrenAges": [
         1
       ] 
     }
   ]
 }' 'https://galaxy.citybreak.com/v2/api/availability/get'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/availability/get",
{
	method: "POST",
	headers: {
	   "ApiKey:" "APIKEY132456789EWOK",
	   "Accept": "application/json",
		 "Accept-Language": "en-US"
	},
	body: JSON.Stringify({
	   "PointOfSalesId": {pointOfSalesId},
	   "Arrival": "2017-10-14T12:27:58.851Z",
	   "Departure": "2017-10-15T12:27:58.851Z",
	   "Currency": "SEK",
	   "PageSize": 20,
	   "Page": 1,
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
    "PointOfSalesId": {pointOfSaleId},
    "Arrival": "2017-10-14T00:00:00Z",
    "Departure": "2017-10-15T00:00:00Z",
    "Currency": "SEK",
    "PageSize": 20,
    "Page": 1,
    "Sort": {
      "Order": 0,
      "Field": "Price"
    },
    "PersonConfigurations": [
      {
        "Adults": 1,
        "ChildrenAges": [
          0
        ]
      }
    ],
    "ContentFilter": null,
    "OutputFilter": null
  },
  "Accommodations": [
    {
      "Id": "cbis:1136433",
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

*NB under active development* This is a **POST** request that requires a filter with a valid (non-expired) SearchId. The filter otherwise behaves the same as it would in the original <a href="https://visit.github.io/galaxy-docs-v2/#Accommodation">Accommodation</a> search. You can see a bare minimum verison of this search in the examples.

### HTTP Request

`POST https://galaxy.citybreak.com/availability/get`

### Query Parameters

Parameter | Description
--------- | -----------
filter | the POST filter
Accept-Language | The language culture (e.g en-us)



## Cabin Search

The cabin search will look for available cabins in the neighburhood of the requested
Arrival/Departure of the stay definition. The result will give you cabins that matches
or partially matches the stay definition. A score will tell how good of a match it was.
You can use the related methods to navigate in the search result until it is resolved
into a bookable match. Once there you can put the selected cabin and stay dates in
the basket.

### How to add a result to basket

#### Call Scan
First you call the Scan method to get perform a search. You will get a partial listing
back describing the first set of results. The `SearchId` will be used in all other methods
to refer back to the original search you made. 
The scan operation will examine dates around the stay (-10 days before arrival and +10 
days after the selected departure).

#### Page through the result
By using the Get method you will be able to page through the result.

#### Get arrival dates in search span
Once you get a result you like and would like to investigate further you can get more
details of the possible stays with that result by calling *arrivaldates*. That will give 
you all valid arrival dates available in scan sector that was used. 

#### Get departure dates 
By calling the *depaturedates*, given an arrival date you will get all valid departures
from that date.

#### List bookable alternatives
By calling *bookablealternatives* you will get back actual bookable items between
a specified arrival and departure. You will get a list of items back. Since a cabin
may be sold under certain conditions, you may get more than one back. 
Each describing a price and the conditions under it will be sold. 
Included subproducts can differ between the items for instance.

#### Add to basket
Once you have a bookable alternative you can add it to the basket by calling
*PUT api/basket/add/cabin/\{basketId\}/\{searchId\}/\{bookKey\}*

### Suggested implementation
Do a scan and sort over `Score` `Descending`. Navigate using the *Get* to find
a result on a page that you would like more detailed information on. 
Keep the search id and go to a page which presents that item in a good way.
Create an arrival calendar by calling *getarrivaldates*. Upon selecting 
an arrival date, populate the departure dates.
When selecting a departure date, call *bookablealternatives* and get the details
and present them with a book button next to them.
Default all calender items with the example dates from the scan.
If you would like to show the next period, you will need to call scan once again
and get the new `ResultId`.

### Scan 
Use this method first to get a `ResultId` to be able to proceed with all other 
operations. 

#### Search parameters
All parameters are submitted through an instance of the CabinSearchFilter object as described below.

|Parameter|Description|
|------|-----|
PointOfSalesId|The point of sales that should be used. It defines the assortment that could be searched.|
Currency|The currency the basket search should deliver results for. It must match the currency your basket is in.
PageSize|The number of results in the return object. It may not exceed 50 and suggested is between 10 and 20.
Page|The page you would like to start with. Normally 0, it will give you the first page with the best matches
Stay|The Stay object describes what types of stay results you would like to get.
Stay.ArrivalDayMask|The arrival day mask, see DayMask below.
Stay.DepartureDayMask|The departure day mask, see DayMask below.
Stay.MinStayLength|The minimum length of stay you require.
Stay.MaxStayLength|The maximum length of stay you require.
Stay.Arrival|The suggested arrival date.
Stay.Departure|The suggested departure date.

#### Using the Stay object
The `arrival` and `depature` makes up a sweet spot span where you would like to arrive.
The search is performed with the focus on that area. 
However you can get results that partially matches that span. 
The `Score` property will tell how good of a match a specific result was. 
It will also give you the best price for the specified stay that the item used to 
calculate the score. 
The example properties on that object will tell which ones it was.

Use the `arrival`/`departure` day mask to create queries to match like short week, 
weekends and such.
For instance, use 0x18 to create results arriving on Thurday or Friday and use departure
mask 0x61 to specify acceptable depatures on Saturday, Sunday or Monday. 
That could be your weekend day filter.

Use the `MinStayLength`/`MaxStayLength` stay to specify an acceptable length of you stay. 
7/7 will give you exactly seven days of stay.
2-3 will restrict the stay to 2 or 3 days. 
That could be used in conjunction with the week days filter.
1/7 will give you results where you could stay anywhere between 1 or 7 days. 
Usually not a very good definition.

Keep in mind that this is only used to give you relevant stay dates as the result.
You can use the get arrival dates and departure dates when you examine a specified 
result to create a bookable result that does not neccisarily matches your 
original constraints. 
So there is certainly no need to use the 1-7 days span to be able to do so later on.


##### Day mask
A bit mask describing which days that are valid for arriving at or depart at. 

|Day|Bit|
|-----|-----|
Monday|0x01
Tuesday|0x02
Wednesday|0x04
Thursday|0x08
Friday|0x10
Saturday|0x20
Sunday|0x40

> Mask examples
>
> <dl>
> <dt>0x7F</dt> <dd>Any day, this is the default if 0 is submitted.</dd>
> <dt>0x18</dt> <dd>Thursday or Friday.</dd>
> <dt>0x0F</dt> <dd>Monday, Tuesday, Wednesday, Thursday or Friday.</dd>
> </dl>

##### Sort definition
The sort definition is used to order the paged results you get. 

|Order|Meaning|
|------|------|
Asc|Ascending - The item with the lowest field value first. Suggested when sorting by Price.
Desc|Descending - The item the highest field value first. Suggested when sorting by Score.

> Valid sort fields
> 
> <dl>
> <dt> Name</dt> <dd>  Sort by the name of the Cabin</dd>
> <dt> Price </dt> <dd> Sort by example price</dd>
> <dt> Random </dt> <dd> Sort by a random order.</dd>
> <dt> Score </dt> <dd>Sort by the relevance of the example stay.</dd>
> </dl>
>
> *Note that the field names are case sensitive.*

Sugested sort order is by `Score`/`Descending`. 
That will give you the most relevant items first. 
Please note that price may give some unintended side effects when using
`MaxStayLength`/`MinStayLength` and `ArrivalDayMask`/`DepartureDayMask` filter. 
The items may not compare well to each other sice one item may have produced 
a result that is shorter than another (hence a different price) or 
using `ArrivalDayMask`/`DepartureDayMask`.
The price may differ heavily if you are in a high season week and low season week. 
Ordering by `Price` is therefor not neccisarily a good sorting for listing 
relevant results. 

#### ContentFilter
The content filter specifies that the search result should be narrowed to certain
results that only matches that filter. See Availability search for specification.

#### ContentOutputFilter
The output filter describes which content that should be included with the item.
See the availability search for specifications.


```shell
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Accept-Language: en-us' --header 'apiKey: APIKEY132456789EWOK' -d '{
{
  "PointOfSalesId": 0,
  "Currency": "SEK",
  "PageSize": 10,
  "Stay": {
    "ArrivalDaysMask": 0x7F, 
    "DepartureDayMask": 0x7F,
    "MinStayLength": 7,
    "MaxStayLength": 7,
    "Arrival": "2018-04-01",
    "Departure": "2018-04-08"
  },
  "PersonConfiguration": {
    "Adults": 2,
    "ChildrenAges": [
      3
    ]
  },
  "Sort": {
    "Order": "Asc",
    "Field": "Score"
  }
} }' 'https://galaxy.citybreak.com/v2/api/availability/cabin/scan'
```

```javascript
var r = fetch("https://galaxy.citybreak.com/v2/api/availability/cabin/scan",
{
	method: "POST",
	headers: {
	    "ApiKey:" "APIKEY132456789EWOK",
	    "Accept": "application/json",
		 "Accept-Language": "en-US"
	},
	body: JSON.Stringify({
  "PointOfSalesId": 0,
  "Currency": "SEK",
  "PageSize": 10,
  "Stay": {
    "ArrivalDaysMask": 0x7F, 
    "DepartureDayMask": 0x7F,
    "MinStayLength": 7,
    "MaxStayLength": 7,
    "Arrival": "2018-04-01",
    "Departure": "2018-04-08"
  },
  "PersonConfiguration": {
    "Adults": 2,
    "ChildrenAges": [
      3
    ]
  },
  "Sort": {
    "Order": "Asc",
    "Field": "Score"
  })  
});
```

> Example of response:

```json
{
  "SearchId": "12313212313",
  "TotalResults": 15,
  "Result": [
    {
      "Id": "cbis:154623",
      "BookingKey": "253-C",
      "Name": "My cabin",
      "Content": {
        "PriceFrom": 0,
        "Images": [
          {
            "Uri": "//images.citybreak.com/image.aspx?ImageId=4014876",
            "IsMain": true,
            "Name": null,
            "Copyright": null,
            "Description": null
          }
        ],
        "Information": [
          {
            "Id": 99,
            "Name": "Name",
            "Value": "My Cabin"
          },
          {
            "Id": 101,
            "Name": "Introduction",
            "Value": "A really nice cabin"
          },
          {
            "Id": 102,
            "Name": "Description",
            "Value": "A cabin located in the centre of all slopes."
          },
          {
            "Id": 100038,
            "Name": "Elevator",
            "Value": "False"
          }
        ],
        "Categories": [
          {
            "Id": 0,
            "Path": "string"
          }
        ],
        "Geos": [
          {
            "Id": 0,
            "Path": "string"
          }
        ],
        "Pois": [
          {
            "Id": 0,
            "Name": "string",
            "Position": {
              "Latitude": 0,
              "Longitude": 0
            }
          }
        ],
        "Position": {
          "Latitude": 0,
          "Longitude": 0
        }
      },
      "Score": 0,
      "ExampleArrival": "2017-12-13T06:13:08.820Z",
      "ExampleDeparture": "2017-12-13T06:13:08.820Z",
      "Extrabeds": 0,
      "MaxPopluationForAnyItem": 0,
      "MaxPopulation": 0,
      "OriginalPrice": 0,
      "Price": 0
    }
  ],
  "SearchContext": { 
        /* Copy of what was sent to the method.
        ...
        */
    },
    "PageSize": 10,
    "Page": 0,
    "PersonConfiguration": {
      "Adults": 2,
      "ChildrenAges": [
        3
      ]
    },
    "Currency": "SEK",
    "ArrivalDayMask": 0x7f,
    "DepartureDayMask": 0x7f,
    "MinStayLength": 7,
    "MaxStayLength": 7,
    "Sort": {
      "Order": "Asc",
      "Field": "Score"
    }
  }
}
```

### Get
This method is used to get a different page of the result.
> POST /api/availability/cabin/get

```json
{
  "Page": 1, /* The second page */
  "PageSize": 10,
  "Sort": {
    "Order": "Desc",
    "Field": "Score"
  },
  "SearchId": "123123132",
  "ContentOutputFilter": {
    "Attributes": [
        99, 101, 102
    ],
    "Categories": true,
    "Geos": true,
    "Pois": true,
    "Position": true
  }
}
```

### Arrival dates
Get a set of valid arrival dates for a specified item.
> GET api/availability/cabin/arrivaldates

Parameters are:
* searchId - From the `result`
* bookKey - From the `result.Result[n].BookKey`
* firstArrival - First acceptable date for the result. 
* lastArrival - Last acceptable date for the result.
* personConfig - Typically the same used in *Scan*

It returns a list of dates that are valid for arrival.

### Departure dates
Get a set of valid departure dates for the specficed item given the arrival date.
> GET api/availability/cabin/departuredates

Parameters are:
* searchId - From the `result`
* bookKey - From the `result.Result[n].BookKey`
* arrival - The specified arrival date from which you would like valid departure dates.
* personConfig - Typically the same used in *Scan*

It returns a set of dates that are valid for departure given the arrival date.

### Get bookable alternatives
> GET api/availability/cabin/bookablealternatives

Parameters are:
* searchId - From the `result`
* bookKey - From the `result.Result[n].BookKey`
* arrival - The specified arrival date.
* departure - The specifeid departure date.
* personConfig - Typically the same used in *Scan*

It returns a list of valid alternatives to book:

```json
[
  {
    "BookId": 0,
    "DiscountInformation": {
      "Name": "string",
      "Description": "string"
    },
    "Arrival": "2018-04-03",
    "Departure": "2018-04-10",
    "Subproducts": [
      {
        "Name": "string",
        "Currency": "string",
        "Description": "string",
        "IncludedInPrice": true,
        "PayOnSite": false,
        "Price": 0
      }
    ],
    "OriginalPrice": 0,
    "Price": 0,
    "RateInformation": {
      "Name": "string",
      "CancellationLatest": "2017-12-13",
      "Terms": "string"
    }
  }
]
```

Use the `BookId` when referring to this specific result when adding it to the basket.

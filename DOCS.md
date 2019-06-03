## GET /v2/:provider
*NOTE: valid providers are currently only `hotelscombined` and `priceline`*

Used to get a list of hotels that have available rooms

**Query Strings**:
```
field           type        description
---------------------------------------
address         string      Address for a specific venue or location. Not as accurate/reliable as latitude and longitude
latitude        float       Latitude of the search center point
longitude       float       Longitude of the search center point
radius          float       Radius from the center point in meters
checkin         string      Check in date. Formats are autodetected but YYYY/MM/DD, YYYY-MM-DD, or Unix timestamps are the most reliable
checkout        string      Check out date. Formats are autodetected but YYYY/MM/DD, YYYY-MM-DD, or Unix timestamps are the most reliable
minprice        float       Minimum price bounds (before taxes and fees)
maxprice        float       Maximum price bounds (before taxes and fees)
language        string      A BCP47 formatted language tag (en, fr, pt-BR, ...). Languages only return data in that language selected if it's available and will fallback to another language, commonly English
currency        string      An ISO4217 formatted currency (CAD, USD, EUR, ...)
guests          int         Number of guests (both adults and children)
rooms           int         Number of rooms needed (for group booking)
limit           int         Number of items that should be shown
page            int         The page number that should be shown. Used in conjunction with limit to provide pagination
sortby          string      Which type of sorting to apply (popularity, review, distance, price, name, or rating)
sortdirection   string      Which way to sort (up/ascending/low/near or down/descending/high/far)
star            []string    Limit to hotels with the given number of stars sent as a list. A star of "2,4" shows only hotels of 2 and 4 stars. 
minstar         int         Limit to hotels with the given number of stars. A minstar of 2 will show hotels with stars of 2,3,4,5.
minrating       float64     Limit to hotels with the given rating score. A minrating of 7.5 will show hotels of 7.5 and above.
amenities       []string    List of amenities you're looking for (gym, free_breakfast, free_cancellation, pool, free_wifi, wifi, food, restaurant, bar, beach, free_parking, parking, ski, bbq, sport, pets, bath, tv, casino, evening_entertainment, spabath, family_rooms, airport_shuttle)
staytype        []string    List of property type/stay types that you're looking for (hotel, inn, motel, hostel, apartment, bnb, house, camping, unique)
```

**Example**:
```
curl "https://api.stay22.com/v2/hotelscombined?latitude=45.5017&longitude=-73.5673&radius=1000&checkin=2018-06-10&checkout=2018-06-12&minprice=0&maxprice=1200&language=en&currency=CAD&guests=2&rooms=1&limit=3&page=1"
```

**Response**:
```
{
  "errors": {},
  "meta": {
    "number_of_nights": 2,
    "total_results": 246,
    "available_results": 58,
    "currency_code": "USD",
    "lowest_rate": 64,
    "highest_rate": 2116
  },
  "results": [
    {
      "id": "hc::1058824", // internal item id built by `<prefix>:<external_id>`
      "link": "https://www.hotelscombined.com/Hotel/Search?a_aid=159522&adults_1=2&checkin=2018-06-10&checkout=2018-06-12&currencyCode=USD&fileName=Hotel_Bonaventure_Montreal&label=stay22&languageCode=en&rooms=1",
      "name": "Hotel Bonaventure Montreal",
      "address": "900 de La Gauchetiere West",
      "latitude": 45.498998,
      "longitude": -73.566466,
      "thumbnails": [
        "https://edge.media.datahc.com/HP278607098.jpg",
        "https://edge.media.datahc.com/HP500047181.jpg",
        "https://edge.media.datahc.com/HP500047182.jpg",
        "https://edge.media.datahc.com/HP500047183.jpg",
        "https://edge.media.datahc.com/HP500047184.jpg",
        "https://edge.media.datahc.com/HP329829604.jpg",
        "https://edge.media.datahc.com/HP264814808.jpg",
        "https://edge.media.datahc.com/HP329829607.jpg",
        "https://edge.media.datahc.com/HP264814801.jpg",
        "https://edge.media.datahc.com/HP264814804.jpg",
        "https://edge.media.datahc.com/HP264814800.jpg",
        "https://edge.media.datahc.com/HP500047185.jpg",
        "https://edge.media.datahc.com/HP500047186.jpg"
      ],
      "images": [
        "https://edge.media.datahc.com/HI278607098.jpg",
        "https://edge.media.datahc.com/HI500047181.jpg",
        "https://edge.media.datahc.com/HI500047182.jpg",
        "https://edge.media.datahc.com/HI500047183.jpg",
        "https://edge.media.datahc.com/HI500047184.jpg",
        "https://edge.media.datahc.com/HI329829604.jpg",
        "https://edge.media.datahc.com/HI264814808.jpg",
        "https://edge.media.datahc.com/HI329829607.jpg",
        "https://edge.media.datahc.com/HI264814801.jpg",
        "https://edge.media.datahc.com/HI264814804.jpg",
        "https://edge.media.datahc.com/HI264814800.jpg",
        "https://edge.media.datahc.com/HI500047185.jpg",
        "https://edge.media.datahc.com/HI500047186.jpg"
      ],
      "rating": 83, // review out of 100
      "review_count": 8030, // number of reviews made
      "rooms": [
        {
          "link": "https://redirect.datahc.com/ProviderRedirect.ashx?key=0.24147267.-1147450411.3.USD.1647704379&source=201-0&a_aid=159552&brandID=481227",
          "provider": {
            "Name": "Booking.com",
            "Logo": "https://cdn.datahc.com/images/providers/logos/BKS.png?cdn=1.0.2018.156002-C48ac5f9007d134aee70d486335bd86e9c161d7dd"
          },
          "name": "Double Room with Two Double Beds - Non-refundable - Free WiFi",
          "rates": [
            {
              "per_night": 278.5,
              "total": 557
            }
          ]
        },
        {
          "link": "https://redirect.datahc.com/ProviderRedirect.ashx?key=0.24147267.-1147450411.4.USD.1158382910&source=201-1&a_aid=159552&brandID=481227",
          "provider": {
            "Name": "Booking.com",
            "Logo": "https://cdn.datahc.com/images/providers/logos/BKS.png?cdn=1.0.2018.156002-C48ac5f9007d134aee70d486335bd86e9c161d7dd"
          },
          "name": "Queen Room with Two Queen Beds - Non-refundable - Free WiFi",
          "rates": [
            {
              "per_night": 286,
              "total": 572
            }
          ]
        },
        {
          "link": "https://redirect.datahc.com/ProviderRedirect.ashx?key=0.33722842.-1147450599.11.USD.256741923&source=201-2&a_aid=159552&brandID=481227",
          "provider": {
            "Name": "Expedia.com",
            "Logo": "https://cdn.datahc.com/images/providers/logos/EXP.png?cdn=1.0.2018.156002-C48ac5f9007d134aee70d486335bd86e9c161d7dd"
          },
          "name": "Room, 2 Double Beds (Free WiFi)",
          "rates": [
            {
              "is_cancellable": true,
              "per_night": 277.5,
              "total": 555
            }
          ]
        },
        {
          "link": "https://redirect.datahc.com/ProviderRedirect.ashx?key=0.33722842.-1147450599.15.USD.1758024999&source=201-3&a_aid=159552&brandID=481227",
          "provider": {
            "Name": "Expedia.com",
            "Logo": "https://cdn.datahc.com/images/providers/logos/EXP.png?cdn=1.0.2018.156002-C48ac5f9007d134aee70d486335bd86e9c161d7dd"
          },
          "name": "Room, 2 Double Beds (Free breakfast, Free WiFi)",
          "rates": [
            {
              "is_cancellable": true,
              "per_night": 328,
              "total": 656
            }
          ]
        },
        {
          "link": "https://redirect.datahc.com/ProviderRedirect.ashx?key=0.39773035.-1147455227.9.USD.1879362991&source=201-4&a_aid=159552&brandID=481227",
          "provider": {
            "Name": "ZenHotels.com",
            "Logo": "https://cdn.datahc.com/images/providers/logos/ZHT.png?cdn=1.0.2018.156002-C48ac5f9007d134aee70d486335bd86e9c161d7dd"
          },
          "name": "Standard Twin Room (2 twin beds)",
          "rates": [
            {
              "per_night": 335,
              "total": 670
            }
          ]
        }
      ],
      "min_rates": {
        "is_cancellable": true,
        "per_night": 277.5,
        "total": 555
      },
      "max_rates": {
        "per_night": 335,
        "total": 670
      }
    }
  ]
}
```

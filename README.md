## food-order

## Create Restaurant 
http://localhost:8081/restaurants/v1/create

#Request:

    {
        "id": 90002,
        "name":"Hyderabad Baryani",
        "description":"Baryani Point Bangalore",
        "address":{
        "id":123,
        "type":"RESTAURANT",
        "street":"Silkboard",
        "city":"Bangalore",
        "state":"Karnataka",
        "pincode":123455
        }
    }

## Get Restaurant

http://localhost:8082/restaurants/v1/get/90002

#Response:

    {
        "id": 90002,
        "name": "Hyderabad Baryani",
        "description": "Baryani Point Bangalore",
        "address": {
            "id": 123,
            "type": "RESTAURANT",
            "street": "Silkboard",
            "city": "Bangalore",
            "state": "Karnataka",
            "pincode": "123455"
        }
    }

## Create Menu

http://localhost:8082/restaurants/v1/create/90001/menu

#Request:

    [
        {
        "id":5001,
        "name":"Chicken Biryani",
        "description":"Non-veg Chicken Biryani",
        "price":300.00,
        "quantity":1
    }
    ]

#Response:

    [
        {
            "id": 5001,
            "restaurantId": 90001,
            "name": "Chicken Biryani",
            "description": "Non-veg Chicken Biryani",
            "price": 300.0,
            "quantity": 1
        }
    ]

#Get Restaurant Menu
http://localhost:8082/restaurants/v1/get/90001/menu

#Response:

    [
        {
            "id": 5001,
            "restaurantId": 90001,
            "name": "Chicken Biryani",
            "description": "Non-veg Chicken Biryani",
            "price": 300.0,
            "quantity": 1
        }
    ]

## Create Order
http://localhost:8081/orders/v1/create

## Order Request

    {
    "id":2,
    "orderNumber":50003,
    "itemList":[
        {
            "id":2001,
            "name":"Non Veg Biryani",
            "description":"Hyderabad Chicken Biryani",
            "price":300.00
        },
        {
            "id":2003,
            "name":"Veg Starter",
            "description":"Spicy veg starter ",
            "price":100.00
        },
        {
            "id":2002,
            "name":"Veg Biryani",
            "description":" Veg Biryani",
            "price":200.00
        }
    ],
    "status":"CREATED",
    "total":630.00,
    "taxPercentage":5.00,
    "totalTaxAmount":30.00,
    "restaurantId":1003,
    "customerId":3003,
    "driverId":4003
    }
    
## Create Order
http://localhost:8081/orders/v1/get/restaurants/1001

## Order Request 

    [
        {
            "id": 1,
            "orderNumber": 50002,
            "createdDate": "2021-05-23T03:40:54.048+00:00",
            "lastUpdatedDate": "2021-05-23T03:40:54.048+00:00",
            "itemList": [
                {
                    "id": 2002,
                    "name": "Veg Biryani",
                    "description": " Veg Biryani",
                    "price": 200.0,
                    "quantity": null
                },
                {
                    "id": 2001,
                    "name": "Non Veg Biryani",
                    "description": "Hyderabad Chicken Biryani",
                    "price": 300.0,
                    "quantity": null
                }
            ],
            "status": "CREATED",
            "total": 325.0,
            "taxPercentage": 5.0,
            "totalTaxAmount": 25.0,
            "restaurantId": 1001,
            "customerId": 3001,
            "driverId": 4001
        },
        {
            "id": 2,
            "orderNumber": 50001,
            "createdDate": "2021-05-23T03:54:22.313+00:00",
            "lastUpdatedDate": "2021-05-23T03:54:22.313+00:00",
            "itemList": [
                {
                    "id": 2003,
                    "name": "Veg Starter",
                    "description": "Spicy veg starter ",
                    "price": 100.0,
                    "quantity": null
                },
                {
                    "id": 2002,
                    "name": "Veg Biryani",
                    "description": " Veg Biryani",
                    "price": 200.0,
                    "quantity": null
                },
                {
                    "id": 2001,
                    "name": "Non Veg Biryani",
                    "description": "Hyderabad Chicken Biryani",
                    "price": 300.0,
                    "quantity": null
                }
            ],
            "status": "CREATED",
            "total": 630.0,
            "taxPercentage": 5.0,
            "totalTaxAmount": 30.0,
            "restaurantId": 1001,
            "customerId": 3002,
            "driverId": 4002
        }
    ]

## Invoice-Service

##Generate Order Invoice Report
    http://localhost:8086/invoices/v1/generateOrder
## Request

    {
       "id":1,
       "orderNumber":200001,
       "createdDate":"2021-05-23T03:40:54.048+00:00",
       "lastUpdatedDate":"2021-05-23T03:40:54.048+00:00",
       "itemList":[
          {
             "id":1,
             "restaurantId":300001,
             "name":"Biryani",
             "description":"Veg Biryani",
             "price":200.00,
             "quantity":1
          },
          {
             "id":2,
             "restaurantId":300001,
             "name":"Non Veg Biryani",
             "description":"Non Veg Biryani",
             "price":300.00,
             "quantity":1
          }
       ],
       "status":"CREATED",
       "taxPercentage":5.00,
       "restaurantId":300001,
       "customerId":987654
    }

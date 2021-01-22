```python
class customer:
    def check_avail(type_list):
        print("check_avail_function")

        final_booking(car_type_ip,rental_list,hatchback,sedan,SUV)
    
        return index_ctype,car_name_ip,car_type_ip, days
    
    def final_booking(car_type_ip,rental_list,hatchback,sedan,SUV):
        print(car_type_ip,"\n",rental_list,"\n",hatchback,"\n",sedan,"\n",SUV)
                
        if "hatchback" in car_type_ip:
            if car_name_ip in hatchback:
                hatchback.remove(car_name_ip)
                rental_list.append(car_name_ip)
        elif "sedan" in car_type_ip:
            if car_name_ip in sedan:
                sedan.remove(car_name_ip)
                rental_list.append(car_name_ip)                
        elif "SUV" in car_type_ip:
            if car_name_ip in SUV:
                SUV.remove(car_name_ip)
                rental_list.append(car_name_ip)                
        return hatchback,sedan,SUV,rental_list
        
    def bill_calc(days,price):
        total = int(days)*int(price)
        return total     
    
class rental:
    def check_rent_list(rental_list):
        print("Rental Cars",rental_list)
        ret_car_nm = input("Choose the car you want to return")
        rental_list.remove(ret_car_nm)
        return rental_list
    
    def bill(days,price):
        total_bill = customer.bill_calc(days,price)
        return total_bill
                
```


```python
import json
# avail_stock_list = ["H1","H2","H3","H4","S1","S2","S3","SU1","SU2","SU3"]
# rental_list = []
type_list = ["hatchback","sedan","SUV"]
less_than_week = ["30","50","100"]
more_than_week = ["25","40","90"]


data_dict = { "data":
                 {
                    "avail_stock_list": ["H1","H2","H3","H4","S1","S2","S3","SU1","SU2","SU3"],
                    "rental_car": [],
                    "customers_list": [],
                    "less_than_week":[],
                    "rental_list":[],
                    "total_list":[],
                    "car_type":
                               { 
                                "type_order":["hatchback","sedan","SUV"],
                                "hatchback":["H1","H2","H3","H4"],
                                "sedan":["S1","S2","S3"],
                                "SUV" : ["SU1","SU2","SU3"]
                               }
                }
            }

# with open("cars.json","w") as f:
#     json.dump(data_dict,f)
while(1):
    with open("cars.json","r") as f:
        data = json.load(f)
    print("First Time Data",data)

    

    print("Welcome To the car World")
    print("Do you want to rent a car OR Return a rented car")
    cust_ip = input("Enter rent or return")
    
    

    # print("Car Types: ",car_type)

    if "rent" in cust_ip:
        car_type_list = data["data"]["car_type"]
        rental_list = data["data"]["rental_car"]
        print("Select Car Type From:", data_dict["data"]["car_type"]["type_order"])
        car_type_ip = input("Enter Car Type")  

        print("Enter Car Name ",car_type_list)
        car_name_ip = input("Enter Car Name")   

        days = int(input("For how many days do you want to rent?")) 

        hatchback = car_type_list["hatchback"]
        sedan = car_type_list["sedan"]
        SUV = car_type_list["SUV"]

        index_ctype = type_list.index(car_type_ip)
        
        if days < 7:
            price = less_than_week[index_ctype]
            print(price)
        if days > 7:
            price = more_than_week[index_ctype]
            
        total = customer.bill_calc(days,price)
        
        customer.final_booking(car_type_ip,rental_list,hatchback,sedan,SUV)
        print("Estimated_Bill: £",total)
        print("rental_list",rental_list)
        print("Available_list: ",hatchback, sedan,SUV)
        data_dict["data"]["rental_list"] = total
        data_dict["data"]["rental_list"] = rental_list
        print(data_dict)
        with open("cars.json","w") as f:
            json.dump(data_dict,f)
    if "return" in cust_ip:
#         rental_list
        rental_list = rental.check_rent_list(rental_list)
        total_bill = rental.bill(days,price)
        print("Total Bill To pay: £",total_bill)
        data_dict["data"]["total_list"] = total_bill
        with open("cars.json","w") as f:
            json.dump(data_dict,f)

# print(data)
```

    First Time Data {'data': {'avail_stock_list': ['H1', 'H2', 'H3', 'H4', 'S1', 'S2', 'S3', 'SU1', 'SU2', 'SU3'], 'rental_car': [], 'customers_list': [], 'less_than_week': [], 'rental_list': [], 'total_list': 300, 'car_type': {'type_order': ['hatchback', 'sedan', 'SUV'], 'hatchback': ['H1', 'H2', 'H3', 'H4'], 'sedan': ['S1', 'S2', 'S3'], 'SUV': ['SU1', 'SU2', 'SU3']}}}
    Welcome To the car World
    Do you want to rent a car OR Return a rented car



```python

```


```python

```

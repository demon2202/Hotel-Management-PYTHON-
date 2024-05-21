# Hotel-Management


### Classes

#### Hotel Class

The `Hotel` class represents a hotel with several attributes and methods.

```python
class Hotel:
    sortParam='name'
    def __init__(self) -> None:
        self.name = ''
        self.roomAvl = 0
        self.location = ''
        self.rating = int
        self.pricePr = 0
```

- **Attributes:**
  - `name`: The name of the hotel.
  - `roomAvl`: The number of available rooms.
  - `location`: The location of the hotel.
  - `rating`: The rating of the hotel.
  - `pricePr`: The price per room.

- **Class Attribute:**
  - `sortParam`: A class-level attribute that determines the sorting parameter (default is `'name'`).

The `__init__` method initializes these attributes with default values.

```python
    def __lt__(self, other):
        return getattr(self, Hotel.sortParam) < getattr(other, Hotel.sortParam)
```

- **`__lt__` Method:**
  - This is a special method used to define the behavior of the less-than operator `<` for `Hotel` objects. It uses the current sorting parameter (`sortParam`) to compare two `Hotel` instances.

```python
    @classmethod
    def sortByName(cls):
        cls.sortParam = 'name'

    @classmethod
    def sortByRate(cls):
        cls.sortParam = 'rating'

    @classmethod
    def sortByRoomAvailable(cls):
        cls.sortParam = 'roomAvl'
```

- **Class Methods:**
  - `sortByName`: Sets `sortParam` to `'name'`.
  - `sortByRate`: Sets `sortParam` to `'rating'`.
  - `sortByRoomAvailable`: Sets `sortParam` to `'roomAvl'`.

These class methods allow changing the sorting parameter at the class level.

```python
    def __repr__(self) -> str:
        return "PRHOTELS DATA:\nHotelName:{}\tRoom Available:{}\tLocation:{}\tRating:{}\tPricePer Room:{}".format(self.name, self.roomAvl, self.location, self.rating, self.pricePr)
```

- **`__repr__` Method:**
  - Provides a string representation of the `Hotel` object, which is useful for printing the object in a readable format.

#### User Class

The `User` class represents a user with several attributes.

```python
class User:
    def __init__(self) -> None:
        self.uname = ''
        self.uId = 0
        self.cost = 0
```

- **Attributes:**
  - `uname`: The username.
  - `uId`: The user ID.
  - `cost`: The booking cost.

```python
    def __repr__(self) -> str:
        return "UserName:{}\tUserId:{}\tBooking Cost:{}".format(self.uname, self.uId, self.cost)
```

- **`__repr__` Method:**
  - Provides a string representation of the `User` object, useful for printing.

### Functions

#### PrintHotelData

Prints the list of hotel objects.

```python
def PrintHotelData(hotels):
    for h in hotels:
        print(h)
```

- **Parameters:**
  - `hotels`: A list of `Hotel` objects.

#### SortHotelByName

Sorts the list of hotels by name and prints the sorted list.

```python
def SortHotelByName(hotels):
    print("SORT BY NAME:")
    Hotel.sortByName()
    hotels.sort()
    PrintHotelData(hotels)
    print()
```

- **Parameters:**
  - `hotels`: A list of `Hotel` objects.

- **Functionality:**
  - Sets the sorting parameter to `name`, sorts the hotels, and prints the sorted list.

#### SortHotelByRating

Sorts the list of hotels by rating and prints the sorted list.

```python
def SortHotelByRating(hotels):
    print("SORT BY A RATING:")
    Hotel.sortByRate()
    hotels.sort()
    PrintHotelData(hotels)
    print()
```

- **Parameters:**
  - `hotels`: A list of `Hotel` objects.

- **Functionality:**
  - Sets the sorting parameter to `rating`, sorts the hotels, and prints the sorted list.

#### PrintHotelBycity

Prints hotels located in a specific city.

```python
def PrintHotelBycity(city, hotels):
    print("HOTELS FOR {} LOCATION ARE:".format(city))
    hotelsByLoc = [h for h in hotels if h.location == city]
    PrintHotelData(hotelsByLoc)
    print()
```

- **Parameters:**
  - `city`: The city to filter hotels by.
  - `hotels`: A list of `Hotel` objects.

- **Functionality:**
  - Filters hotels by location and prints the filtered list.

#### SortByRoomAvailable

Sorts the list of hotels by room availability and prints the sorted list.

```python
def SortByRoomAvailable(hotels):
    print("SORT BY ROOM AVAILABLE:")
    Hotel.sortByRoomAvailable()
    hotels.sort()
    PrintHotelData(hotels)
    print()
```

- **Parameters:**
  - `hotels`: A list of `Hotel` objects.

- **Functionality:**
  - Sets the sorting parameter to `roomAvl`, sorts the hotels, and prints the sorted list.

#### PrintUserData

Prints user booking details with associated hotel names.

```python
def PrintUserData(userName, userId, bookingCost, hotels):
    users = []
    for i in range(3):
        u = User()
        u.uname = userName[i]
        u.uId = userId[i]
        u.cost = bookingCost[i]
        users.append(u)
    for i in range(len(users)):
        print(users[i], "\tHotel name:", hotels[i].name)
```

- **Parameters:**
  - `userName`: List of usernames.
  - `userId`: List of user IDs.
  - `bookingCost`: List of booking costs.
  - `hotels`: List of `Hotel` objects.

- **Functionality:**
  - Creates `User` objects, stores them in a list, and prints each user's details along with the associated hotel name.

#### HotelManagement

Main function to create hotel and user objects, and demonstrate sorting and printing functionalities.

```python
def HotelManagement(userName, userId, hotelName, bookingCost, rooms, locations, ratings, prices):
    hotels = []
    for i in range(3):
        h = Hotel()
        h.name = hotelName[i]
        h.roomAvl = rooms[i]
        h.location = locations[i]
        h.rating = ratings[i]
        h.pricePr = prices[i]
        hotels.append(h)
    print()
    PrintHotelData(hotels)
    SortHotelByName(hotels)
    SortHotelByRating(hotels)
    PrintHotelBycity("Bangalore", hotels)
    SortByRoomAvailable(hotels)
    PrintUserData(userName, userId, bookingCost, hotels)
```

- **Parameters:**
  - `userName`: List of usernames.
  - `userId`: List of user IDs.
  - `hotelName`: List of hotel names.
  - `bookingCost`: List of booking costs.
  - `rooms`: List of room availability numbers.
  - `locations`: List of hotel locations.
  - `ratings`: List of hotel ratings.
  - `prices`: List of prices per room.

- **Functionality:**
  - Creates `Hotel` objects and stores them in a list.
  - Demonstrates various sorting and printing functionalities.

### Usage

```python
if __name__ == '__main__':
    userName = ["U1", "U2", "U3"]
    userId = [2, 3, 4]
    hotelName = ["H1", "H2", "H3"]
    bookingCost = [1000, 1200, 1100]
    rooms = [4, 5, 6]
    locations = ["Bangalore", "Bangalore", "Mumbai"]
    ratings = [5, 5, 3]
    prices = [100, 200, 100]

    HotelManagement(userName, userId, hotelName, bookingCost, rooms, locations, ratings, prices)
```

- **Functionality:**
  - Initializes data for users and hotels.
  - Calls `HotelManagement` to process and display the data.

### Example Output

```
## Example Output
PRHOTELS DATA:
HotelName:H1  Room Available:4  Location:Bangalore  Rating:5  PricePer Room:100
HotelName:H2  Room Available:5  Location:Bangalore  Rating:5  PricePer Room:200
HotelName:H3  Room Available:6  Location:Mumbai  Rating:3  PricePer Room:100

SORT BY NAME:
PRHOTELS DATA:
HotelName:H1  Room Available:4  Location:Bangalore  Rating:5  PricePer Room:100
HotelName:H2  Room Available:5  Location:Bangalore  Rating:5  PricePer Room:200
HotelName:H3  Room Available:6  Location:Mumbai  Rating:3  PricePer Room:100

SORT BY A RATING:
PRHOTELS DATA:
HotelName:H3  Room Available:6  Location:Mumbai  Rating:3  PricePer Room:100
HotelName:H1  Room Available:4  Location:Bangalore  Rating:5  PricePer Room:100
HotelName:H2  Room Available:5  Location:Bangalore  Rating:5  PricePer Room:200

HOTELS FOR Bangalore LOCATION ARE:
PRHOTELS DATA:
HotelName:H1  Room Available:4  Location:Bangalore  Rating:5  PricePer Room:100
HotelName:H2  Room Available:5  Location:Bangalore  Rating:5  PricePer Room:200

SORT BY ROOM AVAILABLE:
PRHOTELS DATA:
HotelName:H1  Room Available:4  Location:Bangalore  Rating:5  PricePer Room:100
HotelName:H2  Room Available:5  Location:Bangalore  Rating:5  PricePer Room:200
HotelName:H3  Room Available:6  Location:Mumbai  Rating:3  PricePer Room:100

UserName:U1  UserId:2  Booking Cost:1000  Hotel name: H1
UserName:U2  UserId:3  Booking Cost:1200  Hotel name: H2
UserName:U3  UserId:4  Booking Cost:1100  Hotel name: H3

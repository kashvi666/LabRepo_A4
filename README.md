# LabRepo_A4
class Flight:
    def __init__(self, flight_id, origin, destination, price):
        self.flight_id = flight_id
        self.origin = origin
        self.destination = destination
        self.price = price

class FlightTable:
    def __init__(self):
        self.flights = []

    def add_flight(self, flight):
        self.flights.append(flight)

    def search_by_city(self, city):
        result = []
        for flight in self.flights:
            if flight.origin == city or flight.destination == city:
                result.append(flight)
        return result

    def search_by_origin(self, origin):
        result = []
        for flight in self.flights:
            if flight.origin == origin:
                result.append(flight)
        return result

    def search_between_cities(self, origin, destination):
        result = []
        for flight in self.flights:
            if flight.origin == origin and flight.destination == destination:
                result.append(flight)
        return result

def print_flights(flights):
    if not flights:
        print("No flights found.")
    else:
        for flight in flights:
            print(f"Flight ID: {flight.flight_id}, From: {flight.origin}, To: {flight.destination}, Price: {flight.price}")

# Creating flight objects
flights_data = [
    ("AI161E90", "BLR", "BOM", 5600),
    ("BR161F91", "BOM", "BBI", 6750),
    ("AI161F99", "BBI", "BLR", 8210),
    ("VS171E20", "JLR", "BBI", 5500),
    ("AS171G30", "HYD", "JLR", 4400),
    ("AI131F49", "HYD", "BOM", 3499)
]

flight_table = FlightTable()
for flight_data in flights_data:
    flight = Flight(*flight_data)
    flight_table.add_flight(flight)

# User interaction
while True:
    print("\nSearch options:")
    print("1. Flights for a particular City")
    print("2. Flights From a city")
    print("3. Flights between two given cities")
    print("4. Quit")
    choice = int(input("Enter your choice: "))

    if choice == 1:
        city = input("Enter city: ")
        result = flight_table.search_by_city(city)
        print_flights(result)
    elif choice == 2:
        origin = input("Enter origin city: ")
        result = flight_table.search_by_origin(origin)
        print_flights(result)
    elif choice == 3:
        origin = input("Enter origin city: ")
        destination = input("Enter destination city: ")
        result = flight_table.search_between_cities(origin, destination)
        print_flights(result)
    elif choice == 4:
        break
    else:
        print("Invalid choice. Please select a valid option.")

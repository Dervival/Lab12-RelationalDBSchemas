# Lab12-RelationalDBSchemas
Quick repository for today's work on 1-24.

## Relational Databases and Schemas
For this project, we needed to create a schema given the following information:

1. The hotel can hold many guests at any given time, in fact guests can come and go as they please…..asynchronously :)
1. The hotel is named “Async Inn” and has many nationwide locations. Each location will have a name, city, state, address, and phone number.
1. Async Inn prides themselves on their unique layout designs of each hotel room. They advertise as it being your “apartment for the night”. This means they have invested a lot of resources into how each room looks and feels. Some have one bedroom, others have 2 bedrooms, while a few are more of a cozy studio. The team mentioned that they like to label each room with a nickname to better tell the difference between each of the layouts and amenities each room has to offer. (for example, the Seattle location has two 2-bedroom suites, but one is named “Seahawks Snooze” while the other is named “Restful Rainier”, each with their own amenities.)
1. They also take pride in the amenities that each room has to offer. This can consist of features like “air conditioning”, “coffee maker”, “ocean view”, “mini bar”, the list goes on…They requested that they would like the amenities associated with each of the rooms as they do vary.
1. The rooms vary in price, per location, as well as per room number. They also have a few rooms that they want to advertise as pet friendly.
1. The number of rooms for each hotel varies. Some hotels have only a few rooms, while others may have dozens.

Additionally, we were required to implement the following:
- (1) Joint Entity Table with Payload
- (1) Pure Join Table
- (1) Enum

## Schema by Blaise Clarke and Andrew Hinojosa:
[!Whiteboard drawing of proposed schema](https://github.com/Dervival/Lab12-RelationalDBSchemas/blob/master/AsyncSchemaDrawing.jpg);

## Schema Component Explanation
Hotel Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id: Primary key for the table. Represents a unique numeric (possibly enumerated) value for each entry in the table.
	- Name: Name of the hotel instance. Default is presumably "Async Inn". String type. Does not need to be unique.
	- City: Name of the city of the hotel instance. String type.
	- State: State that the hotel instance resides in. String type. 
	- Address: Address of the hotel instance. String type.
	- Phone: Phone number for the front desk of the hotel instance. String type.
- Relations
	- Reservations - From the first data point, I had thought that it would be good to be able to link customers to hotels in some way. A person can go to several different instances of hotels at different times, and a hotel can contain several guests, so this needs to be represented as a many:many relationship - using a reservation table as either a pure join table or a joint-entity with payload seemed like a reasonable approach. One-to-Many, as a single hotel can have many reservations, but a reservation is specific to a given hotel.
	- HotelConfigs - Additionally, I wanted to represent room configurations as its own table, and a given room configuration can be in several hotels (and vice versa). This is just a direct table linking the RoomConfig table and Hotel tables to allow that relationship. One-to-Many, since a hotel can have several configurations, but each entry should only link to a single combination of hotel and room configuration.
- Navigation
	- Reservations - To traverse between the Hotel table to Customer, CheckIn, and CheckOut tables.
	- HotelConfigs - To traverse between the Hotel table to RoomConfig or Room tables.

Reservation Table:
- Primary Motivation: 
- Properties:
	- Id: Primary key for the table. Represents a unique numeric value for a given reservations. Integer type.
	- HotelId: Part of the composite key for the table, along with the CustomerId and CheckInId. Repr
	- CustomerId
	- CheckInId
	- CheckOutId
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

Customer Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

CheckIn Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

CheckOut Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

	Hotel Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

	Hotel Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

	Hotel Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs

Hotel Table:
- Primary Motivation: Several hotels need to be tracked for the Async Inn chain - ergo, we should have a table whose rows each represent a specific instance of a hotel chain.
- Properties:
	- Id
	- Name
	- City
	- State
	- Address
	- Phone
- Relations
	- Reservations
	- HotelConfigs
- Navigation
	- Reservations
	- HotelConfigs


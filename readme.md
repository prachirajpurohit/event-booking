# Event Booking System Backend


## Stack: 

Node.js, Express, MongoDB, Mongoose, JWT Authentication


## Users:

- ORGANIZER → can create/update events

- CUSTOMER → can browse events and book tickets

## Key Features

- Authentication & Authorization

- JWT-based login/register

- Role-based middleware: requireRole("ORGANIZER") / requireRole("CUSTOMER")

- Password change functionality

## Events

`POST /events → create new event (organizer only)`

`PUT /events/:id → update event (organizer only)`

## Bookings

POST /events/:id/book → book tickets (customer only)

Ticket availability checked automatically

Background Tasks (simulated)

Booking confirmation → console log after booking

Event update notification → console log after event update

In production, these would be handled with job queues like BullMQ or RabbitMQ.


## Design Decisions

Role enums in ALL CAPS (ORGANIZER, CUSTOMER) → ensures middleware consistency

JWT payload contains only userId and role → lightweight, no DB call per request

Async background tasks use setTimeout → satisfies assignment without adding Redis/Bull complexity

Atomic ticket update → simple decrement ensures available tickets remain accurate
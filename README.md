# Airbnb Clone Project

## About the Project
The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security. This project enables learners to understand complex architectures, workflows, and collaborative team dynamics while building a scalable web application.

## Project Goals
- **User Management**: Implement a secure system for user registration, authentication, and profile management.
- **Property Management**: Develop features for property listing creation, updates, and retrieval.
- **Booking System**: Create a booking mechanism for users to reserve properties and manage booking details.
- **Payment Processing**: Integrate a payment system to handle transactions and record payment details.
- **Review System**: Allow users to leave reviews and ratings for properties.
- **Data Optimization**: Ensure efficient data retrieval and storage through database optimizations.

## Technology Stack
- **Django**: A high-level Python web framework used for building the RESTful API.
- **Django REST Framework**: Provides tools for creating and managing RESTful APIs.
- **PostgreSQL**: A powerful relational database used for data storage.
- **GraphQL**: Allows for flexible and efficient querying of data.
- **Celery**: For handling asynchronous tasks such as sending notifications or processing payments.
- **Redis**: Used for caching and session management.
- **Docker**: Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.

## Team Roles
- **Backend Developer**: Responsible for implementing API endpoints, database schemas, and business logic.
- **Database Administrator**: Manages database design, indexing, and optimizations.
- **DevOps Engineer**: Handles deployment, monitoring, and scaling of the backend services.
- **QA Engineer**: Ensures the backend functionalities are thoroughly tested and meet quality standards.

## Database Design
To ensure the Airbnb clone is functional and scalable, we will implement a relational database with the following key entities:

1. **Users**
This entity stores information about the users of the application, including guests and property owners.

- **id**: A unique identifier for each user.

- **username**: A unique name used for login.

- **email**: The user's email address, also used for authentication.

- **password_hash**: A secure hash of the user's password.

- **created_at**: The timestamp when the user account was created.

2. **Properties**
This entity represents the accommodations that are available for booking.

- **id**: A unique identifier for each property.

- **title**: The name or title of the property (e.g., "Cozy Downtown Apartment").

- **description**: A detailed description of the property.

- **price_per_night**: The cost to book the property for one night.

- **location**: The address or location of the property.

- **owner_id**: A foreign key linking to the Users entity, representing the owner of the property.

3. **Bookings**
This entity tracks the reservations made by users for specific properties.

- **id**: A unique identifier for each booking.

- **user_id**: A foreign key linking to the Users entity, representing the guest who made the booking.

- **property_id**: A foreign key linking to the Properties entity, representing the booked property.

- **check_in_date**: The date when the booking starts.

- **check_out_date**: The date when the booking ends.

- **total_price**: The total cost of the booking.

4. **Reviews**
This entity stores feedback and ratings provided by users after a stay.

- **id**: A unique identifier for each review.

- **booking_id**: A foreign key linking to the Bookings entity.

- **rating**: A numerical rating (e.g., 1 to 5).

- **comment**: The text of the review.

- **created_at**: The timestamp when the review was submitted.

5. **Payments**
This entity handles the transaction details for each booking.

- **id**: A unique identifier for each payment record.

- **booking_id**: A foreign key linking to the Bookings entity.

- **amount**: The amount of the payment.

- **status**: The current status of the payment (e.g., "pending," "completed," "failed").

- **transaction_id**: A unique ID from the payment gateway.

- **payment_date**: The timestamp when the payment was processed.

**Entity Relationships**
- Users and Properties: A *User* can be the owner of multiple *Properties*. This is a one-to-many relationship. The *owner_id* in the *Properties* table links to the *id* of the *Users* table.

- Users and Bookings: A *User* can create multiple *Bookings*. This is a one-to-many relationship. The *user_id* in the *Bookings* table links to the *id* of the *Users* table.

- Properties and Bookings: A *Property* can have multiple *Bookings*. This is a one-to-many relationship. The *property_id* in the *Bookings* table links to the *id* of the *Properties* table.

- Bookings and Reviews: A *Booking* can have at most one *Review*. This is a one-to-one relationship. The *booking_id* in the *Reviews* table links to the *id* of the *Bookings* table.

- Bookings and Payments: A *Booking* can have one or more *Payments* (e.g., a deposit and a final payment). For simplicity, we can treat this as a one-to-one relationship where a *Booking* has one *Payment*. The *booking_id* in the *Payments* table links to the *id* of the *Bookings* table.

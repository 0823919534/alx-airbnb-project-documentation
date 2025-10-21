# Airbnb Clone Backend Requirements

## 1. User Authentication
**Description:** Users can register, login, and manage their accounts.  
**Endpoints:**
- POST /api/register — Create a new user
- POST /api/login — Authenticate user and return token
- GET /api/user/{id} — Retrieve user info
- PUT /api/user/{id} — Update user info
- DELETE /api/user/{id} — Delete user account

**Input/Output:**
- Registration: irst_name, last_name, email, password → user_id, 	oken
- Login: email, password → 	oken
- Update: irst_name, last_name, phone_number → updated user object

**Validation:**
- Email must be unique and valid
- Password minimum 8 characters
- Required fields cannot be empty

**Performance:** Handle 100 concurrent users per second

---

## 2. Property Management
**Description:** Hosts can create, read, update, and delete property listings.  
**Endpoints:**
- POST /api/properties — Create a property
- GET /api/properties — List all properties
- GET /api/properties/{id} — Retrieve single property
- PUT /api/properties/{id} — Update property
- DELETE /api/properties/{id} — Delete property

**Input/Output:**
- Property: 	itle, description, price_per_night, max_guests, edrooms, athrooms, listing_type → property_id
- Response: Property object with property_id and timestamps

**Validation:**
- Price must be positive
- Max guests ≥ 1
- Title cannot be empty

**Performance:** Support 5000 properties and 200 requests/sec

---

## 3. Booking System
**Description:** Guests can book properties and manage reservations.  
**Endpoints:**
- POST /api/bookings — Create booking
- GET /api/bookings — List all bookings
- GET /api/bookings/{id} — Retrieve booking details
- PUT /api/bookings/{id} — Update booking
- DELETE /api/bookings/{id} — Cancel booking

**Input/Output:**
- Booking: property_id, guest_id, start_date, end_date → ooking_id
- Response: Booking object with 	otal_price and status

**Validation:**
- end_date must be after start_date
- Check property availability
- Guest cannot book own property

**Performance:** Handle 100 bookings per minute with real-time availability checks

---

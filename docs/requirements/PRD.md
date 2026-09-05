# ShopFlow — Product Requirements Document (PRD)

**Organization:** RanjanTechLabs  
**Product:** ShopFlow  
**Version:** 1.0  
**Status:** Draft  
**Product Type:** Multi-category E-commerce Platform

---

## 1. Product Overview

ShopFlow is a multi-category e-commerce platform that allows customers to discover products, manage shopping carts, place orders, make payments, and track deliveries.

The MVP will operate as a single-seller platform. The architecture should be designed so that a multi-seller marketplace can be introduced in the future without requiring a complete system redesign.

---

## 2. Business Objectives

The objectives of ShopFlow are to:

- Provide customers with a convenient online shopping experience.
- Allow customers to discover and purchase products online.
- Allow administrators to manage products, inventory, customers, and orders.
- Provide secure authentication and authorization.
- Support multiple payment methods.
- Provide order, shipping, return, and refund workflows.
- Support promotional campaigns and discount management.
- Build a maintainable and scalable software system.

---

## 3. User Roles

### 3.1 Guest

A guest user can:

- Browse products.
- Browse categories.
- Search products.
- Filter and sort products.
- View product details.

A guest cannot:

- Place an order.
- Access customer account information.
- Submit product reviews.

### 3.2 Customer

A customer can:

- Register and log in.
- Manage their profile.
- Manage delivery addresses.
- Browse and search products.
- Filter and sort products.
- Add products to cart.
- Update and remove cart items.
- Manage wishlist.
- Checkout.
- Make payments.
- Place orders.
- View order history.
- Cancel eligible orders.
- Request returns.
- View refund information.
- Review eligible products.
- Receive notifications.

### 3.3 Admin

An administrator can:

- Manage products.
- Manage categories.
- Manage product variants.
- Manage inventory.
- Manage customers.
- Manage orders.
- Manage returns and refunds.
- Manage promotions.
- View sales information.
- Manage platform operations.

---

# 4. Functional Requirements

## FR-01 — User Registration

The system shall allow customers to create an account using required personal information and credentials.

## FR-02 — User Authentication

The system shall authenticate registered users securely.

## FR-03 — Role-Based Authorization

The system shall restrict protected operations according to user roles.

Supported roles:

- CUSTOMER
- ADMIN

## FR-04 — Product Catalog

The system shall allow users to browse products organized into categories.

## FR-05 — Product Variants

A product may have multiple variants.

Examples:

- Size
- Color
- Storage
- Configuration

Each variant may maintain independent inventory.

## FR-06 — Product Search

Customers shall be able to search products using relevant product information such as product name.

## FR-07 — Product Filtering and Sorting

Customers shall be able to filter and sort products using supported attributes such as:

- Category
- Price
- Rating
- Availability

## FR-08 — Pagination

Product listing APIs shall support pagination.

## FR-09 — Shopping Cart

Customers shall be able to:

- Add products or product variants.
- Change quantities.
- Remove items.
- View cart contents.
- View calculated cart totals.

## FR-10 — Wishlist

Customers shall be able to save products to a wishlist and remove them later.

## FR-11 — Address Management

Customers shall be able to:

- Add addresses.
- Update addresses.
- Delete addresses.
- Select an address during checkout.

## FR-12 — Checkout

Customers shall be able to:

- Review cart items.
- Select a delivery address.
- Review shipping charges.
- Apply eligible promotions.
- Select a payment method.
- Review the final order amount.
- Place an order.

## FR-13 — Payments

ShopFlow shall support:

- Cash on Delivery.
- Online payment.

The initial development environment may use a simulated online payment system.

A real payment gateway may be integrated in a later phase.

## FR-14 — Orders

Customers shall be able to:

- Place orders.
- View order history.
- View order details.
- View order status.
- Cancel eligible orders.

## FR-15 — Order Status

Orders shall support appropriate lifecycle statuses.

Example:

    PLACED
    CONFIRMED
    PROCESSING
    SHIPPED
    OUT_FOR_DELIVERY
    DELIVERED
    CANCELLED

## FR-16 — Shipping

ShopFlow shall maintain shipping information for orders.

The system shall support:

- Shipping address.
- Shipping charge.
- Shipment information.
- Tracking number.
- Delivery status.

The initial version will use ShopFlow-managed shipping.

External shipping-provider integration should be possible in the future.

## FR-17 — Inventory Management

Inventory shall be maintained at the product-variant level.

The system shall support:

- Stock quantity.
- Restocking.
- Stock deduction after successful purchases.
- Stock restoration after eligible returns.
- Manual stock adjustments.

## FR-18 — Inventory Movement Tracking

The system shall maintain inventory movement records.

Examples:

- PURCHASE
- RESTOCK
- RETURN
- ADJUSTMENT

## FR-19 — Promotions

The system shall support:

- Product discounts.
- Category discounts.
- Coupon codes.
- Percentage discounts.
- Fixed-amount discounts.
- Minimum order value.
- Promotion start date.
- Promotion end date.
- Usage limits.
- Per-customer usage limits.

## FR-20 — Reviews and Ratings

Customers shall be able to review eligible products they have purchased.

The system shall prevent unauthorized users from submitting reviews for products they have not purchased.

## FR-21 — Returns

Customers shall be able to request returns for eligible orders/items.

A return request shall include:

- Order information.
- Product/item information.
- Return reason.
- Additional details where required.

## FR-22 — Return Management

Administrators shall be able to:

- Review return requests.
- Approve returns.
- Reject returns.
- Track return status.

## FR-23 — Refunds

The system shall support refunds for eligible cancelled or returned orders/items.

Refund information and status shall be recorded.

## FR-24 — Notifications

ShopFlow shall support:

### Email notifications

Examples:

- Account registration.
- Order confirmation.
- Payment confirmation.
- Order shipment.
- Order delivery.
- Order cancellation.
- Refund confirmation.

### In-app notifications

Examples:

- Order status changes.
- Payment updates.
- Promotional notifications.
- Important account notifications.

## FR-25 — Admin Product Management

Administrators shall be able to:

- Create products.
- Update products.
- Remove/deactivate products.
- Manage product variants.
- Assign categories.
- Manage product information.

## FR-26 — Admin Category Management

Administrators shall be able to:

- Create categories.
- Update categories.
- Activate/deactivate categories.

## FR-27 — Admin Order Management

Administrators shall be able to:

- View orders.
- View order details.
- Update appropriate order statuses.
- Manage order operations.

## FR-28 — Admin Customer Management

Administrators shall be able to:

- View customers.
- View customer information.
- Manage customer account status where appropriate.

## FR-29 — Admin Dashboard

The admin dashboard shall provide basic business information such as:

- Total orders.
- Total customers.
- Product count.
- Sales information.
- Order status summary.

---

# 5. Non-Functional Requirements

## NFR-01 — Security

- Passwords must never be stored as plain text.
- Authentication must be secure.
- Protected APIs must require appropriate authorization.
- Sensitive configuration must not be committed to source control.
- Customers must only access their own private data.

## NFR-02 — Performance

Frequently accessed operations such as product browsing and searching should provide acceptable response times under expected load.

## NFR-03 — Scalability

The architecture should allow the system to grow as the number of users, products, and orders increases.

## NFR-04 — Maintainability

The backend should follow separation of responsibilities and clean architecture principles.

The application should maintain clear separation between:

- Controllers
- Services
- Repositories
- DTOs
- Entities

## NFR-05 — Reliability

Critical operations such as order creation, payment processing, and inventory updates must maintain data consistency.

## NFR-06 — Availability

The system should remain available during normal operating conditions.

## NFR-07 — Auditability

Important business operations should maintain appropriate records for troubleshooting and operational purposes.

---

# 6. Business Rules

## BR-01 — Stock Availability

A customer cannot purchase more units than the available inventory.

## BR-02 — Inventory Consistency

Inventory updates during order processing must maintain data consistency even when multiple customers attempt to purchase the same product simultaneously.

## BR-03 — Order Cancellation

Customers can cancel only orders that are eligible for cancellation.

## BR-04 — Return Eligibility

Returns are allowed only for eligible products/orders and within the configured return period.

## BR-05 — Review Eligibility

Only customers who purchased an eligible product may submit a review.

## BR-06 — Promotion Validity

Expired or inactive promotions cannot be applied.

## BR-07 — Promotion Conditions

A promotion can only be applied when all configured conditions are satisfied.

## BR-08 — Coupon Usage

Coupon usage must respect configured usage limits and customer-specific limits.

## BR-09 — Customer Data Isolation

A customer cannot access another customer's private orders, addresses, payments, or account information.

## BR-10 — Administrative Access

Administrative operations must be restricted to authorized administrators.

---

# 7. MVP Scope

The initial MVP shall include:

- User registration and authentication.
- Role-based authorization.
- Product catalog.
- Categories.
- Product variants.
- Product search.
- Filtering and sorting.
- Pagination.
- Cart.
- Wishlist.
- Address management.
- Checkout.
- Cash on Delivery.
- Simulated online payment.
- Orders.
- Shipping.
- Inventory management.
- Promotions and coupons.
- Product reviews.
- Returns.
- Refunds.
- Email notifications.
- In-app notifications.
- Admin dashboard.

---

# 8. Future Scope

The following features are outside the initial MVP:

- Multi-vendor marketplace.
- Real shipping-provider integration.
- Advanced recommendation engine.
- Advanced analytics.
- Mobile applications.
- Multiple currencies.
- International shipping.
- AI-powered product recommendations.
- Advanced fraud detection.
- Advanced seller management.

---

# 9. Technology Direction

The initial technology direction is:

### Frontend

- React
- Tailwind CSS

### Backend

- Java
- Spring Boot
- Spring Security

### Database

- MySQL

### ORM

- JPA
- Hibernate

### Authentication

- JWT

### Build Tool

- Maven

### Version Control

- Git
- GitHub

### API Testing

- Postman

Additional technologies such as Redis, Docker, messaging systems, cloud storage, and CI/CD will be evaluated during the architecture and implementation phases.

---

# 10. Assumptions and Constraints

- ShopFlow initially operates as a single-seller platform.
- The system should be designed for future marketplace expansion.
- Online payment will initially be simulated during development.
- Shipping will initially be managed by ShopFlow.
- The project is developed as a portfolio project following industry-style development practices.
- Features will be implemented incrementally using Agile/Scrum.

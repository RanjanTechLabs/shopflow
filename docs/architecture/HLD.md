# ShopFlow — High-Level Design (HLD)

**Organization:** RanjanTechLabs  
**Product:** ShopFlow  
**Version:** 1.0  
**Status:** Draft

---

# 1. System Overview

ShopFlow is a multi-category e-commerce platform designed using a microservices architecture.

The system allows customers to browse products, manage carts, place orders, make payments, track deliveries, request returns, and receive notifications.

Administrators can manage products, inventory, orders, customers, promotions, and returns.

The initial system is a single-seller platform but the architecture is designed to support future marketplace capabilities.

---

# 2. Architecture Style

ShopFlow uses a **Microservices Architecture**.

Each microservice represents a specific business capability and owns its associated data.

The services communicate using:

- REST for synchronous communication.
- Apache Kafka for asynchronous event-driven communication.

---

# 3. High-Level Architecture

```text
                           ┌────────────────────┐
                           │    React Client    │
                           │   + Tailwind CSS   │
                           └─────────┬──────────┘
                                     │
                                  HTTPS
                                     │
                                     ▼
                           ┌────────────────────┐
                           │  API Gateway       │
                           │ Spring Cloud       │
                           │ Gateway             │
                           └─────────┬──────────┘
                                     │
             ┌───────────────┬───────┼────────┬───────────────┐
             │               │       │        │               │
             ▼               ▼       ▼        ▼               ▼
       ┌──────────┐   ┌──────────┐ ┌─────┐ ┌────────┐ ┌──────────┐
       │   Auth   │   │ Product  │ │Cart │ │ Order  │ │ Payment  │
       │ Service  │   │ Service  │ │Svc  │ │Service │ │ Service  │
       └────┬─────┘   └────┬─────┘ └──┬──┘ └───┬────┘ └────┬─────┘
            │              │          │         │           │
            ▼              ▼          ▼         ▼           ▼
        auth_db        product_db   cart_db   order_db   payment_db


                         ┌─────────────────────┐
                         │  Inventory Service  │
                         └──────────┬──────────┘
                                    │
                                    ▼
                              inventory_db


                         ┌─────────────────────┐
                         │ Notification Service│
                         └──────────┬──────────┘
                                    │
                                    ▼
                              notification_db


                    ┌────────────────────────────┐
                    │       Apache Kafka         │
                    │     Event Infrastructure   │
                    └────────────────────────────┘


                    ┌────────────────────────────┐
                    │      Service Discovery     │
                    │          Eureka            │
                    └────────────────────────────┘


                    ┌────────────────────────────┐
                    │    Spring Cloud Config    │
                    │          Server            │
                    └────────────────────────────┘



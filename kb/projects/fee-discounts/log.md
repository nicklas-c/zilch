# Fee Discounts

## Context

A project to offer discounted membership fees to customers, with potential to extend to other fee types in future.

### Background (from #fee-discounts-design-group, Jan–Mar 2026)

* Marcin Żołna proposed a work group with Abhishek Chatterjee and tech leads from Merchant, Payments, and Decisioning to design a discount solution for memberships (and potentially other fees).
* Crinan (Product) owns the membership discounts initiative and shared a product document outlining use cases — discounted memberships and a potential Deliveroo-style voucher system.
* Abhishek Chatterjee drafted an architecture proposing two services:
    * **discount-service** — to be owned by the owner of fee-service.
    * **offer-service** — to be owned by the owner of product-service.
* The group agreed to start with just the offer-service in the short term; discount-service would follow.
* Charging for physical cards was prioritised above discounts (estimated £312k EBITDA impact vs £145k for discounts).
* Ownership of the discounts service still needs to be discussed with engineering leadership.
* An implementer for the offer-service is still needed.

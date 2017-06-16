# Effective Dating (of Goods and Services)

by George Craig, [georgeacraig@gmail.com](georgeacraig@gmail.com), 14-Jun-2017

### Definition

Effective - applicable, valid, enforced, available

### Problem Set

Sometimes, we need to manage data (from all kinds of verticals) and have dates assigned to them which tracks their validity, applicability, enforcement, and availability, etc. "Effective Dating" is this mechanism, often seen in many DatawareHouses as another (temporal) dimension. Simply stated, you will typically see a StartDate, EndDate, or both columns in these tables. Applying this knowledge to the Object layer in a logical and useful manner is the goal of this addition. As a result, simplified date handling will result and less spaghetti code should emerge. Less conditionals will be in your code base and you'll be able to answer questions that relate to "when" events occur.

### Managing Date Ranges, Start Dates, and End Dates with Objects

This design pattern or collective pattern will attempt to manage objects (and subsequent data records in RDBMS/NoSQL/NewSQL, etc.) such that it is simple to obtain a Collection of applicable or "Effective" objects that are valid and used in a given use case. This need and implementation is used in many different domains from Insurance, Banking, Finance, Inventory Management, MRP/ERP/HRM, B2B, and E-Commerce. Almost any project can encounter the use case of Effective Dating.

#### Example Use Case and Flow:

* Let's pretend we are operating an E-Commerce site and want to promote a given item in an advertisement during a given time frame - Mother's Day.
* We'll only showcase this new advertisement for a month before Mother's Day since it makes sense to display it during this time frame.
* Our code base is of high quality and doesn't require hard coding many "If" statements all throughout the display logic. (Think: Code Complete).
* An "Effective Dating" mechanism will allow us to specify in our data the StartDate and EndDate and a few more attributes, but the beauty comes from our Object layer; it will automatically handle the display via querying an "Advertisement" object isInEffect(), returning a true.
* With this pattern, Abstraction, and Polymorphism, our goal is to centralize the manipulation of dates and their relationship to a given Person, Item, Promotion, Discount, Style, etc. How an organization applies it will be the same across domains; yet, which objects it leverages against will be their business revenue generator.
* In GoF speak, your implementation will be simple Template extensions of the Interfaces and Abstract classes we have defined. Their relationships will make it simple for your team to plug in the objects you want to manage via time.
* A JSON configuration file may simplify the initial definition, configuration and use of this framework.

### UML Model

![Effective Dating UML](/etc/effective-dating.jpg?raw=true "Effective Dating UML")

### UML Model Explanation

TBA

### References

"Effective Dating" has roots in ETL (Extraction, Transformation, Loading) and DatawareHousing; all beginning in RDBMS. 

The following article, despite written specifically for Human Resources lays out the complex issue of dates and when/how they may become an issue or applied. It's not a simple conundrum of when a date is applicable for a given person, item, service or event. Retroactive, ranges, forecasting, etc. all have been a challenge for us at one time or another. 

#1 below will be the first deliverable in this effort.

### The Future Of HRM Software: Effective Dating
[http://infullbloom.us/1055/the-future-of-hrm-software-effective-dating/](http://infullbloom.us/1055/the-future-of-hrm-software-effective-dating/)

1. Effective and correction dating consistency
2. Default Dates
3. Prospective and retroactive processing
4. Effective-dated event processing
5. Forecasting and simulation
6. Date Ranges: Multiple chronological perspectives at one time
7. Historical Data
8. Case Management Data

### Versioning

**Pass 1** - The first design and attempt of this pattern will simply include three use cases:

1. **StartDate** - when a given service will begin or become effective.
2. **EndDate** - when a given (already effective) service will become unavailable.
3. **StartDate/EndDate** *(Potentially multiple records)* - when a given service will come in and out of organizational support.

Thus, expect to see at minimum three Java Methods: startDate(), endDate(), isInEffect() in main use. *As of this writing, this design is in flux and more ground is to be covered.*

**Pass 2** - The second design, or grown approach, may include Generics to simplify the design and offer greater flexibility and applicability across any business vertical.

**TODO:** Nice to haves: Annotations, AOP, Java 8&9 code
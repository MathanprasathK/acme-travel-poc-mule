# Acme Travel RESTFul API

This Mule runtime based RESTFul API provides the Flight related information as Acme decided to tap into the Mobile market. This API retrieves the Flight and other data stored in MySQL database.
For the purpose of this PoC and to verify this assessment seamlessly, the RESTFul API is neither protected by any Token Policies nor SLAs for that matter.

## Key Design decisions made

1. The Key design decisions are based on RESTFul API best practices and experience in developing commercial grade REST APIs.

2. As the requirement is to build a RESTFul API, the design first approach was followed. Started off by designing RAML(1.0) based API Specification on Anypoint Platform hence the APIKIT Router component leveraged in the Mule flow.
 
3. As per the best practices, The design strategy is more to align with HTTP Endpoints CRUD operations.

4. The API version v1.0 was decided as it is a best practice and helpful to manage the lifecycle of an API once it's made available to customers/public.

5. The requirement is to retrieve flights available --- GET :/flights resource(root level resource) was decided. And as per the RESTFul best practices the resource must be a plural noun as opposed to be singular noun or verb

6. The sub-resource -- /{flightCode}/destinations was decided as it makes more sense to group it under /flights resource (root level resource). Again as per the best practices of grouping sub-resourcs under same collection.

7. As the requirement is to retrieve a PAGINATED list of destinations, the LIMIT and optional OFFSET query parameters have been decided to be used.

8. Since the PoC requirement is to simulate the price and seats available based on airline, the PATCH verb was decided as opposed to PUT which expects full Payload to be used.

9. As the requirement is to add a new flight, the POST Verb is quite naturaly comes handy to be used by submitting a payload.

10. Since JSON is light weight data format, human readable and also has become a universal choice for REST APIs hence the decision was made in favour of JSON data format.

11. DWL2.0 was used everywhere in the Mule flow as it is very powerful, performant and handy when it comes to transformations hence the decision was made.

12. YAML based Global configurations were leveraged to separate the Env specific context from business logic/flow.

## Endpoints exposed

**Base path :** /api/acme-travel/v1.0

HTTP Method | Endpoint name | Example
---|---|---

**GET** | /flights?date={date} | /flights?date=2020-04-06

**GET** | /flights/{flightCode}/destinations?limit={value}&offset={value} | /flights/328/destinations?limit=100&offset=50

**PATCH** | /flights/{flightCode}/prices | /flights/BA001/prices

**POST** | /flights | /flights


## Deployment Notes

1. Please aware Its maven based Mule project hence once imported into Anypoint studio can be deployed quickly provided PORT 8081 is free.

2. To test the API quickly, I have developed ready to run POSTMAN collections and also environments.
Hence kindly import both the POSTMAN collections and environments file into your POSTMAN.
Once your done you can run the entire collection in one ago in POSTMAN collection runner.

3. The POSTMAN Test scripts written tells whether the exectuion of endpoints are of successfull.

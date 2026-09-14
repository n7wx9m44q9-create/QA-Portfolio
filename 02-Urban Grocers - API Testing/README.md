# Urban Grocers — API Testing

## What is this?

A QA testing project completed as part of the TripleTen QA Tester Bootcamp.

The project focused on API testing for the Urban Grocers application, validating request structure, input data, business rules, and response behavior across different endpoints.

## Product & Functionality Under Test

Urban Grocers is an application that manages products and kits, including functionality related to adding products to kits and calculating delivery availability and costs.

The testing included:

- Adding products to kits
- Product quantity validation
- Product ID validation
- Delivery calculation
- Delivery time validation
- Product count and weight validation
- Required request fields
- Response status codes and JSON data
- Delivery cost and business rules

## Objective

To validate API behavior against the defined requirements and identify defects related to input validation, business rules, response handling, and data integrity.

Testing focused particularly on boundary values, invalid input, missing data, and unexpected request structures.

## Scope

Testing included:

- Positive and negative API testing
- Equivalence Partitioning
- Boundary Value Analysis
- JSON request and response validation
- HTTP status code validation
- Required field validation
- Data type validation
- Business rule validation
- Response data validation
- Defect reporting in Jira

## Artifacts

- Test cases covering positive, negative, boundary, and equivalence scenarios
- API request and response evidence
- Bug reports documented in Jira
- Screenshots supporting reported defects

## Key Decisions

The test scenarios prioritized areas where invalid input could affect data integrity or produce incorrect business behavior.

Boundary values and invalid data types were given particular attention, especially for delivery time, product quantity, and product weight.

## Results

The testing identified multiple defects involving:

- Incorrect validation of data types
- Negative and zero values being accepted
- Invalid boundary values being processed incorrectly
- Missing required fields being accepted
- Incorrect HTTP responses
- Incorrect delivery cost calculations
- Business rules not being properly enforced

The defects were documented in Jira with reproduction steps, expected and actual results, and supporting evidence.

## What I Would Improve

For a future iteration, I would expand automated API coverage for the most critical validation and business-rule scenarios and add automated regression checks for previously identified defects.

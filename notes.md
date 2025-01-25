---
title: Notes
description: 
published: true
date: 2025-01-25T08:12:12.784Z
tags: notes
editor: markdown
dateCreated: 2025-01-22T21:49:35.207Z
---

# iliad technical test
## Context
The XXX team needs a system to monitor and manage daily user orders. Your task is to design and implement the backend according to the specified requirements.
![system-big-picture.png](/notes/system-big-picture.png)

## Assumptions
Assume there is a frontend that interacts with your APIs and implements the following functionalities:
1. **Order Viewing Page:** Includes filters for date and the ability to search by name and description.
2. **Detailed Order View:** Displays order information along with associated products.
3. **Order Management:** Allows creating, editing or deleting an order.

## Objectives
1. Design and develop a RESTful backend using PHP and a web framework such as Symfony, Laravel, or similar.
2. Use an ORM like Doctrine or similar for database management.
3. Stock Management:
	1. Implement logic to track and manage product stock levels.
  Hint: Think about how stock levels should be managed when orders are created ormodified and how to handle concurrency issues if multiple orders might affect stock simultaneously.
4. Write tests and documentation to ensure code quality.
5. Optional – Efficient Search: Enhance order search functionality by integrating tools like Elasticsearch, Meilisearch or a similar indexing solution to manage efficient searching and filtering.
6. Optional: Configure the project to be runnable in a containerized environment (e.g., Docker).

## Delivery Instructions
- Git Repository: Create a Git repository and include all necessary instructions to start the project (README.md).
- Project Setup: The README.md should contain detailed instructions for setting up the development environment, running the project and executing tests.
- Testing: Provide test coverage and include instructions on how to run the tests.
- Optional – Docker: Include the necessary Docker files and ensure the entire setup can be executed (e.g., docker compose).

## Evaluation
Your solution will be evaluated based on the following criteria:
- Correctness and completeness of the RESTful API implementation.
- Proper and functional setup configuration.
- Code quality and adherence to design principles and best practices in web development.
- Coverage and quality of tests.
- Documentation and clarity of instructions provided

## Purpose of the Test
The aim of this test is not only to assess your technical skills but also to give you the opportunity to express yourself freely. We want to see how you approach a real project, organize your work, and solve problems.

Good luck and do your best! *(thanks)*

[features](/notes/features)
[symfony_configuration](/notes/symfony_configuration)
[Wiki_configuration](/notes/Wiki_configuration)
## Documenting APIs Effectively
1. Course Overview
2. Why Is It Critical to Document APIs?
  - Introduction
  - Version Check
    - OpenAPI 3.1.0+
  - Understanding the Fundamentals of an API
  - What Are the Benefits of Web APIs?
  - Why Must You Document Your Web APIs?ß
  - Documenting Your APIs with the OpenAPI Specification
    - Introducing the OpenAPI Specification
    - Documenting Foundational API Details 
    - Documenting API Paths and Components
    - Documenting API Errors
        ```
            components: {
                securitySchemes: {
                bearerAuth: {
                    type: 'http',
                    scheme: 'bearer',
                    bearerFormat: 'JWT',
                    description: 'JWT Bearer token authentication'
                }
                },
                schemas: {
                    EvaluationProcess: evaluationProcessSchema,
                    Group: groupSchema,
                    NotFoundResponses: NotFoundResponseSchema,
                    SimpleError: simpleErrorSchema
                }
            },        
        ```
        ```
            404: {
                description: 'Invalid query parameters',
                content: {
                    'application/json': {
                    schema: NotFoundResponseSchema,
                    $ref: '#/components/responses/NotFoundResponse
                    }
                }
            },
        ```
    - Documenting API Versioning
  - Using Tooling with the OpenAPI Specification
    - Understanding the OpenAPI Tooling Landscape
    - Swagger Overview
    - Postman Overview
    - Redocly Overview
    - Backstage Overview
  - Creating a Developer Portal
    - Getting Started with an API Developer Portal
    - Creating Content for a Developer Portal

## Getting Started with Swagger 2 Tools
  1. Course Overview
  2. Introductionsws
    - Version Check: Swagger 2.0
    - Introduction:
      - Swagger API 2011
      - OpenAPI 2015
      - Swagger = OpenAPI 2016
      - OpenAPI 3.0 2017
    - The Swagger Tools
      - Swagger Editor
      - Swagger UI
      - Swagger Inspector: postman
      - Swagger Codegen
      - SwaggerHub

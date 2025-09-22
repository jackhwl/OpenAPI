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
      - Swagger 2.0 = OpenAPI 2.0 2016
      - OpenAPI 3.0 2017
    - The Swagger Tools
      - Swagger Editor
        - https://github.com/swagger-api/swagger-editor
      - Swagger UI
      - Swagger Inspector: postman
      - Swagger Codegen
      - SwaggerHub
    - Setup Free Swagger Account
    - The Demo Code
  3. Crete OpenAPI Documents with Swagger Editor
    - Navigating the Swagger Editor
    - OpenAPI 2.0: Vision and Info
        ```
        openapi: '3.0'

        info:
        version: '1.0.0'
        title: Customer API
        description: This is the Customer API.
        termsOfService: terms
        contact:
            name: Wenlin Huang
            url: http://www.wenlin.com
            email: jack@gmail.com
        license:
            name: MIT
            url: http://opensource.org/licenses/MIT
        ```
    - OpenAPI 2.0: Paths and GET Operation
        ```
        paths:
            /customer:
                get:
                summary: read a customer's data
                operationId: getCustomer
                description: "This operation provides a view, The operation uses the customers id to identify the query string"
                responses:
                    200:
                    description: OK
        ```
    - OpenAPI 2.0: Produces, Consumes and Parameters 
        ```
          parameters: 
            - in: query
            name: customerId
            description: pass an optional customerid
            required: true
            content:
        ```
    - OpenAPI 2.0: Response

## OpenAPI Specification and Swagger Tools - Zero to Master
  - Section 1: Introduction to OpenAPI Specification
  - Section 2: Getting Started with OpenAPI specification in code first scenario
  - Section 3: Getting Started with penAPI specification in design first scenario
    - Writing an minimal OpenAPI Specification document
      - https://editor.swagger.io/
      ```
      openapi: 3.0.3
      info:
        title: A minimal OpenAPI document
        version: 0.0.1
      path: {}
      ```
    - Deep dive on info, Contact, License objects
        ```
        openapi: 3.0.3
        info:
        title: EasyShop Products APIs Definition
        description: |
                Using this OpenAPI specification, any consumer can understand the APIs that are exposed by EazyShop
        termsOfService: https://easyshop.com/terms/
        contact:
            name: API Support
            url: https://www.easyshop.com/support
            email: support@easyshop.com
        license:
            name: EasyShop License
            url: https://www.easyshop.com/licenses/LICENSE-2.0.html
        version: 0.0.1
        paths: {}
        ```
    - Understanding & writing server details inside OpenAPI specification
        ```
        servers:
        - url: https://development.easyshop-server.com/v1
            description: Dvelopment server
        - url: https://staging.easyshop-server.com/v1
            description: Staging server
        - url: https://api.easyshop-server.com/v1
            description: Production server
        - url: https://{username}.server.com:{port}/{version}
            variables:
            username:
                default: demo
                description: This value is assigned by the service provider
            port:
                enum:
                - "8443"
                - "443"
                default: "8443"
            version:
                default: v1
        paths: {}
        ```
    - Deep dive on Paths inside Open API specifications
        - Introduction to Paths inside Open API Specification
        - Writing our first path inside Open API Specification
        ```
          paths:
            /categories:
                get:
                summary: List all categories
                description: Returns the list of of categories supported by EazyShop
                responses:
                    '200':
                    description: A list of categories
                    content:
                        application/json:
                        schema:
                            type: array
                            items:
                            type: object
                            properties:
                                categoryId:
                                type: integer
                                name:
                                type: string
        ```
        - Exploring our first path inside Swagger UI
        - Describing Query parameters inside Open API specification
            ```
            get:
                summary: List all categories
                description: Returns the list of of categories supported by EazyShop
                parameters:
                - name: categoryId
                  in: query
                  schema:
                    type: integer
                    minimum: 100
                    maximum: 1000
                  example: 101
            ```
        - Demo of Try it out inside Swagger UI
        - Assignment to build an GET API that supports path params
        - Assignment solution to build an GET API that supports path params
        ```
          /categories/{categoryId}:
            get:
              summary: List all categories
              description: Returns the list of of categories supported by EazyShop
              parameters:
              - name: categoryId
                in: path
                required: true
                schema:
                  type: integer
                  minimum: 100
                  maximum: 1000
                example: 101
              responses:
                '200':
                  description: A list of categories
                  content:
                    application/json:
                      schema:
                        type: object
                        properties:
                          categoryId:
                            type: integer
                          name:
                            type: string
        ```
        - Assignment to build product related APIs
        - Assignment solution to build product related APIs
        ```
          /products:
            get:
              summary: List all products
              description: |
                    Returns the list of of products supported by EazyShop
              parameters:
              - name: categoryId
                in: query
                schema:
                  type: integer
                  minimum: 100
                  maximum: 1000
                example: 101
              responses:
                '200':
                  description: A list of products
                  content:
                    application/json:
                      schema:
                        type: array
                        items:
                          type: object
                          properties:
                            productId:
                              type: integer
                            name:
                              type: string
                            price:
                              type: number
                            categoryName:
                              type: string
                            quantity:
                              type integer
          /products/{productId}:
            get:
              summary: Return product details
              description: Returns the product details from EazyShop
              parameters:
              - name: productId
                in: path
                required: true
                schema:
                  type: integer
                  minimum: 100
                  maximum: 1000
                example: 101
              responses:
                '200':
                  description: Return product details
                  content:
                    application/json:
                      schema:
                        type: object
                        properties:
                          productId:
                            type: integer
                          name:
                            type: string
                          price:
                            type: number
                          categoryName:
                            type: string
                          quantity:
                            type integer
        ```
        - Describing HTTP POST API inside Open API specification
        ```
         /orders:
           post:
             summary: Create Order
             description: |
               Post order details to EazyShop for processing
               and shipping
             requestBody:
               content:
                 application/json:
                   schema:
                     type: object
                     properties:
                       products:
                         type: array
                         items:
                           type: object
                           properties:
                             productId:
                               type: integer
                             name:
                               type: string
                             price:
                               type: number
                             categoryName:
                               type: string
                             quantity:
                               type: integer
                       address:
                         type: object
                         properties:
                           addressLine:
                             type: string
                           city:
                             type: string
                           state:
                             type: string
                           zipcode:
                             type: string                      
             responses:
               '201':
                 description: Order created sucessfully
                 content:
                   application/json:
                     schema:
                       type: object
                       properties:
                         orderId:
                           type: integer        
        ```
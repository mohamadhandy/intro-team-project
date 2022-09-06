openapi: 3.0.3
info:
  title: Swagger Open API for POS Celerates 2022 - OpenAPI 3.0
  description: |-
    This is an API documentation POS Celerates 2022 based on the OpenAPI 3.0 specification.  You can find out more about
    Swagger at [https://swagger.io](https://swagger.io). In the third iteration of the pet store, we've switched to the design first approach!
    You can now help us improve the API whether it's by making changes to the definition itself or to the code.
    That way, with time, we can improve the API in general, and expose some of the new features in OAS3.

  termsOfService: http://swagger.io/terms/
  contact:
    email: apiteam@swagger.io
  license:
    name: Apache 2.0
    url: http://www.apache.org/licenses/LICENSE-2.0.html
  version: 1.0.11
externalDocs:
  description: Find out more about Swagger
  url: http://swagger.io
servers:
  - url: https://petstore3.swagger.io/api/v3
tags:
  - name: User
    description: Operations about User
  - name: Products
    description: Operations about Products
paths:
  /logout:
    get:
      tags:
        - User
      summary: Logs out current logged in user session
      description: ''
      operationId: logoutUser
      parameters: []
      responses:
        default:
          description: successful operation
  /login:
    post:
      tags:
        - User
      summary: User login
      description: user login with email and password.
      operationId: loginUser
      requestBody:
        description: user login object
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/LoginUser'
      responses:
        200:
          description: Successful Operation
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseUserLoginSuccess'
        401:
          description: Unauthorized user
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseUnauthorizedUser'
        400:
          description: Error client side
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseErrorUser'
  /users:
    post:
      tags:
        - User
      summary: Register user
      description: Register user
      operationId: createUser
      requestBody:
        description: Created user object
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/BodyRegisterUser'
      responses:
        201:
          description: successful Register user
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseRegisterUserSuccess'
        400:
          description: error Register user
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseErrorUsers'
    get:
      tags:
        - User
      summary: Get all user
      description: get all user
      operationId: readUser
      responses:
        200:
          description: successful get all user
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseUsers'
        400:
          description: error Register user
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseRegisterUserError'
  /users/{user_id}/products:
    get:
      tags:
        - Products
      summary: Get products (this action must be logged in first)
      description: ''
      operationId: getUserByName
      parameters:
        - name: user_id
          in: path
          description: 'Need parameter user_id'
          required: true
          schema:
            type: string
      responses:
        200:
          description: successful get all product
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductsSuccess'          
        400:
          description: error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductsError'
    post:
      tags:
        - Products
      summary: Create product (this action must be logged in first)
      description: This can only be done by the logged in user.
      operationId: createProduct
      parameters:
        - name: user_id
          in: path
          description: user_id required
          required: true
          schema:
            type: string
      requestBody:
        description: Body Create Product
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/ProductsBody'
      responses:
        201:
          description: successful create product
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseCreateProductsSuccess'          
        400:
          description: error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseCreateProductsError'
  /users/{user_id}/products/{product_id}:
    get:
      tags:
        - Products
      summary: Get detail product (this action must be logged in first)
      description: ''
      operationId: get detail product
      parameters:
        - name: user_id
          in: path
          description: user_id required
          required: true
          schema:
            type: string
        - name: product_id
          in: path
          description: 'Need parameter product_id'
          required: true
          schema:
            type: string
      responses:
        200:
          description: successful get detail product
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductSuccess'          
        400:
          description: error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductsError'
    delete:
      tags:
        - Products
      summary: Delete product by id (this action must be logged in first)
      description: ''
      operationId: deleteProductById
      parameters:
        - name: user_id
          in: path
          description: user_id required
          required: true
          schema:
            type: string
        - name: product_id
          in: path
          description: 'Need parameter product_id'
          required: true
          schema:
            type: string
      responses:
        200:
          description: successful get detail product
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductDelete'          
        400:
          description: error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductsError'
    put:
      tags:
          - Products
      summary: Update product by id (this action must be logged in first)
      description: 'Update product by id'
      operationId: updateProductById
      parameters:
        - name: user_id
          in: path
          description: user_id required
          required: true
          schema:
            type: string
        - name: product_id
          in: path
          description: 'Need parameter product_id'
          required: true
          schema:
            type: string
      responses:
        200:
          description: successful get detail product
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductSuccess'          
        400:
          description: error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResponseProductsError'
components:
  schemas:
    Order:
      type: object
      properties:
        id:
          type: integer
          format: int64
          example: 10
        petId:
          type: integer
          format: int64
          example: 198772
        quantity:
          type: integer
          format: int32
          example: 7
        shipDate:
          type: string
          format: date-time
        status:
          type: string
          description: Order Status
          example: approved
          enum:
            - placed
            - approved
            - delivered
        complete:
          type: boolean
      xml:
        name: order
    Customer:
      type: object
      properties:
        id:
          type: integer
          format: int64
          example: 100000
        username:
          type: string
          example: fehguy
        address:
          type: array
          xml:
            name: addresses
            wrapped: true
          items:
            $ref: '#/components/schemas/Address'
      xml:
        name: customer
    Address:
      type: object
      properties:
        street:
          type: string
          example: 437 Lytton
        city:
          type: string
          example: Palo Alto
        state:
          type: string
          example: CA
        zip:
          type: string
          example: '94301'
      xml:
        name: address
    Category:
      type: object
      properties:
        id:
          type: integer
          format: int64
          example: 1
        name:
          type: string
          example: Dogs
      xml:
        name: category
    Products:
      type: object
      properties:
        product_id:
          type: integer
          format: int64
          example: 1
        name:
          type: string
          example: Coklat Pocky
        price:
          type: integer
          example: 12000
        stock:
          type: integer
          example: 123
        merchant_id:
          type: integer
          description: Merchant id
          format: int64
          example: 1
      xml:
        name: product
    ProductsBody:
      type: object
      properties:
        name:
          type: string
          example: Coklat Pocky
        price:
          type: integer
          example: 12000
        stock:
          type: integer
          example: 123
        merchant_id:
          type: integer
          description: Merchant id
          format: int64
          example: 1
      xml:
        name: product
    LoginUser:
      type: object
      properties:
        email:
          type: string
          example: adminggudang@celerates.com
        password:
          type: string
          example: '123456'
      xml:
        name: loginuser
    MetaCreateSuccess:
      type: object
      properties:
        code:
          type: integer
          example: 201
        status:
          type: string
          example: 'success'
        message:
          type: string
          example: 'Example Message'
      xml:
        name: loginuser
    MetaSuccess:
      type: object
      properties:
        code:
          type: integer
          example: 200
        status:
          type: string
          example: 'success'
        message:
          type: string
          example: 'Example Message'
      xml:
        name: loginuser
    MetaError:
      type: object
      properties:
        code:
          type: integer
          example: 400
        status:
          type: string
          example: 'error'
        message:
          type: string
          example: 'Example Message'
      xml:
        name: loginuser
    MetaUnauthorized:
      type: object
      properties:
        code:
          type: integer
          example: 401
        status:
          type: string
          example: 'error'
        message:
          type: string
          example: 'Example Message'
      xml:
        name: loginuser
    User:
      type: object
      properties:
        user_id:
          type: integer
          format: int64
          example: 1
        name:
          type: string
          example: Admin Gudang
        email:
          type: string
          example: adminggudang@celerates.com
        password:
          type: string
          example: '123456'
        role:
          type: integer
          example: 2
        merchant_id:
          type: integer
          description: Merchant id
          format: int64
          example: 1
      xml:
        name: user
    LoginUserToken:
      type: object
      properties:
        user_id:
          type: integer
          format: int64
          example: 1
        name:
          type: string
          example: Admin Gudang
        email:
          type: string
          example: adminggudang@celerates.com
        password:
          type: string
          example: '123456'
        role:
          type: integer
          example: 2
        merchant_id:
          type: integer
          description: Merchant id
          format: int64
          example: 1
        token:
          type: string
          example: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
      xml:
        name: user
    BodyRegisterUser:
      type: object
      properties:
        name:
          type: string
          example: Admin Gudang
        email:
          type: string
          example: adminggudang@celerates.com
        password:
          type: string
          example: '123456'
        role:
          type: integer
          example: 2
        merchant_id:
          type: integer
          description: Merchant id
          format: int64
          example: 1
      xml:
        name: user
    ResponseUserLoginSuccess:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaSuccess'
        data:
          $ref: '#/components/schemas/LoginUserToken'
    ResponseUnauthorizedUser:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaUnauthorized'
        data:
          type: object
          example: null
      xml:
        name: user
    ResponseErrorUser:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaError'
        data:
          type: object
          example: null
      xml:
        name: user
    ResponseRegisterUserSuccess:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaCreateSuccess'
        data:
          $ref: '#/components/schemas/BodyRegisterUser'
      xml:
        name: user
    ResponseRegisterUserError:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaError'
        data:
          type: object
          example: null
      xml:
        name: user
    ResponseUsers:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaSuccess'
        data:
          type: array
          xml:
            wrapped: true
          items:
            $ref: '#/components/schemas/User'
      xml:
        name: user
    ResponseErrorUsers:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaError'
        data:
          type: object
          example: null
      xml:
        name: user
    ResponseProductsSuccess:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaSuccess'
        data:
          type: array
          xml:
            wrapped: true
          items:
            $ref: '#/components/schemas/Products'
      xml:
        name: products
    ResponseProductsError:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaError'
        data:
          type: object
          example: null
      xml:
        name: products
    ResponseCreateProductsSuccess:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaCreateSuccess'
        data:
          $ref: '#/components/schemas/Products'
      xml:
        name: products
    ResponseCreateProductsError:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaError'
        data:
          type: object
          example: null
      xml:
        name: products
    ResponseProductSuccess:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaSuccess'
        data:
          $ref: '#/components/schemas/Products'
      xml:
        name: products
    ResponseProductDelete:
      type: object
      properties:
        meta:
          $ref: '#/components/schemas/MetaSuccess'
        data:
          type: object
          example: null
      xml:
        name: products
    Tag:
      type: object
      properties:
        id:
          type: integer
          format: int64
        name:
          type: string
      xml:
        name: tag
    Pet:
      required:
        - name
        - photoUrls
      type: object
      properties:
        id:
          type: integer
          format: int64
          example: 10
        name:
          type: string
          example: doggie
        category:
          $ref: '#/components/schemas/Category'
        photoUrls:
          type: array
          xml:
            wrapped: true
          items:
            type: string
            xml:
              name: photoUrl
        tags:
          type: array
          xml:
            wrapped: true
          items:
            $ref: '#/components/schemas/Tag'
        status:
          type: string
          description: pet status in the store
          enum:
            - available
            - pending
            - sold
      xml:
        name: pet
  requestBodies:
    Pet:
      description: Pet object that needs to be added to the store
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/Pet'
        application/xml:
          schema:
            $ref: '#/components/schemas/Pet'
    UserArray:
      description: List of user object
      content:
        application/json:
          schema:
            type: array
            items:
              $ref: '#/components/schemas/User'
  securitySchemes:
    petstore_auth:
      type: oauth2
      flows:
        implicit:
          authorizationUrl: https://petstore3.swagger.io/oauth/authorize
          scopes:
            write:pets: modify pets in your account
            read:pets: read your pets
    api_key:
      type: apiKey
      name: api_key
      in: header

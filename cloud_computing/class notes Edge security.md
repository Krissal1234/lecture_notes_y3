
API gateways

reverse proxy servers
- They intercept requests from clients before they reach the actual web server, this can help manage load, improve security and increase efficiency by cachine or compressing responses


request handling
- This involves
request brokering

Extended reverse proxy functionality
- Api gateways can handle additioanl operations such as logging, filtering HTTP headers   and query strings, implementing rate limiting and circuit breaking, balancing load across servers

KrakenD
- This is a tool that supports creating API gateways with a focus on performance and simplicity. It allows for declarative configuration
- enhances standard proxy servers with additional capabilities suitable for modern architectrures

![[Pasted image 20240512195713.png]]
**Endpoint Matching and Backend Forwarding with Header Filtering**:

- **Endpoint Matching**: The example shows how KrakenD configures an endpoint `/supu` that handles `GET` requests. This demonstrates KrakenD's ability to match incoming API requests to configured routes.
- **Backend Forwarding**: Once a match is found, KrakenD forwards the request to a specified backend service. In the example, requests to `/supu` are forwarded to `http://127.0.0.1:8000` and specifically to the path `/_debug/supu`. This illustrates how KrakenD redirects traffic based on the configuration.
- **Header Filtering**: The example includes `input_headers`, specifying that only `Authorization` and `Content-Type` headers will be included in the requests forwarded to the backend. This feature is crucial for maintaining security and data integrity by ensuring that only necessary headers are passed along with the request.
### Slide 64: KrakenD iii/x

**Support for Request Path Parameters and Response Field Filtering**:

- **Request Path Parameters**: The slide shows configuration for dynamic request handling using path parameters. The endpoint `/github/{user}` dynamically handles requests based on the `{user}` parameter. This feature allows KrakenD to process requests with varying path values efficiently.
- **Response Field Filtering**: After the backend responds, KrakenD can filter which fields in the response are relayed back to the client. In this case, only the fields `authorizations_url` and `code_search_url` are allowed through. This is particularly useful for limiting the exposure of sensitive data and reducing the payload size sent to clients.


![[Pasted image 20240512195921.png]]
### Slide 65: KrakenD iv/x - Rate Limiting and Circuit Breaking

**Rate Limiting**:

- **Purpose**: Prevents overuse of resources by limiting how many requests a user or service can make within a certain period.
- **Configuration Example**:
    - `"max_rate": 2` indicates the maximum number of requests allowed per second.
    - `"capacity": 2` refers to the burst capacity, allowing short bursts of requests up to this limit, beyond the steady rate limit.

**Circuit Breaking**:

- **Purpose**: Protects the system during high load or partial failure by temporarily disabling the service.
- **Configuration Example**:
    - `"interval": 60` specifies the time window in seconds for monitoring failures before the circuit breaker resets.
    - `"timeout": 10` is the duration in seconds that the circuit breaker waits before attempting to close (allow requests) after opening.
    - `"max_errors": 1` sets the number of errors that will trigger the circuit breaker to open.

These features help maintain the stability and availability of services by managing unexpected spikes in traffic and preventing cascading failures in interconnected services.

### Slide 66: KrakenD v/x - Authentication and Role-Based Access Control (RBAC)

**Authentication and RBAC**:

- **Purpose**: Secures API access by ensuring that only authenticated and authorized users can access specific resources.
- **Configuration Example**:
    - `"alg": "RS256"` specifies the algorithm for signing the JSON Web Tokens (JWTs) used in authentication.
    - `"audience": ["http://api.example.com"]` defines the intended recipients of the token.
    - `"roles_key": "http://api.example.com/custom/roles"` indicates the claim key used to store user roles within the token.
    - `"roles": ["user", "admin"]` lists the roles permitted to access the endpoint.
    - `"jwk_url": "https://albert-test.auth0.com/.well-known/jwks.json"` provides the URL for the JSON Web Key Set (JWKS) that contains the public keys used to verify the JWT signatures.

![[Pasted image 20240512200139.png]]
### Slide 67: KrakenD vi/x - TLS Termination and Web Browser Security

**TLS Termination**:

- **Purpose**: To secure communications between clients and the server by encrypting the data transmitted over the network. This process involves KrakenD handling the decryption of TL,S-encrypted traffic coming into the gateway and then passing the unencrypted traffic to the internal services.
- **Configuration Example**:
    - `"tls"`: Configures the paths to the public and private key files (`cert.pem` and `key.pem`), enabling TLS for incoming connections.

**Web Browser Security**:

- **Cross-Origin Resource Sharing (CORS)**:
    - Allows specifying which domains can access resources. This example shows configuration for allowing methods like POST and GET from specific origins, which controls which requests are allowed from different domains.
- **Browser Security Features**:
    - `"browser_xss_filter": true`: Enables built-in protections against cross-site scripting (XSS) attacks.
    - `"content_security_policy"`: Specifies which sources the client browsers are allowed to load resources from, which helps prevent various types of attacks including data injection attacks.
    - Additionally, settings for HTTP Public Key Pinning (`hpkp`) and report URLs for violations suggest a robust setup to enforce and monitor security policies.

### Slide 68: KrakenD vii/x - Demo: Configuring and Using KrakenD

**Demonstration of API Gateway Configuration**:

- **Purpose**: Shows how to configure KrakenD to route API requests effectively using its JSON-based configuration system.
- **Configuration Example**:
    - Defines the API gateway setup with specific endpoints (`/api/v1/books`) and the backend services these endpoints communicate with (`springbooksro-svc` and `springbooks-svc`).
    - Demonstrates advanced routing and caching features such as `cache_ttl` for caching responses, request method configurations, and query string parameters handling, which optimize the performance and control of API traffic.

**Key Takeaways**:

- The combination of TLS termination and advanced browser security settings provides a comprehensive security framework that protects both the data in transit and the users interacting with the application.
- The demo configuration illustrates the flexibility and power of KrakenD in managing complex API routing scenarios, showing its effectiveness in a microservices architecture by directing traffic based on the API endpoint structure and method.

![[Pasted image 20240512200743.png]]
### Slide 71: IAM i/xix - Identity and Access Management

**Authentication**:

- **Purpose**: To prove the identity of users trying to access the system. It's the first step in securing access to resources.
- **Common Methods**:
    - **Username/Password**: The most basic and widely used form of authentication.
    - **Certificates**: Uses digital certificates that involve public key infrastructure (PKI) to prove identity securely. It's more secure than traditional password authentication.
- **Authentication Factors**:
    - **Something You Know**: A password or PIN.
    - **Something You Have**: A security token or mobile device.
    - **Something You Are**: Biometric data such as fingerprints or retinal scans.
- **Multi-factor Authentication (MFA)**: Combines two or more independent credentials for enhanced security. While it increases security, it can also be seen as an inconvenience to some users, potentially reducing its adoption.
- **Risk-based Authentication**: Adjusts authentication requirements based on the assessed risk level of the access request, thus balancing security and user convenience.

### Slide 72: IAM ii/xix - Authorization

**Authorization**:

- **Purpose**: Determines what authenticated users are allowed to do by managing permissions and access rights.
- **Key Concepts**:
    - **Mandatory Access Control (MAC)**: Access permissions are managed centrally, typical in high-security environments. It restricts entity’s capabilities based on information security policies.
    - **Discretionary Access Control (DAC)**: Allows the resource owner to decide on access permissions, commonly used in less stringent environments.
    - **Role-Based Access Control (RBAC)**: Access rights are assigned based on roles within an organization, and permissions to perform certain operations are assigned to specific roles.
    - **Attribute-Based Access Control (ABAC)**: Determines access based on attributes (or policies), which can include user attributes, resource attributes, and environment conditions.
- **Security Principles**:
    - **Principle of Least Privilege**: Users are given the minimum level of access necessary to perform their functions.
    - **Segregation of Duties**: Divides roles and responsibilities to reduce the risk of fraudulent activity.
    - **Escalation of Privilege Avoidance**: Prevents users from granting themselves higher access privileges, either directly or indirectly.

![[Pasted image 20240512205534.png]]### Slide 74: IAM iii/xix - JSON Web Tokens (JWT)

**Overview of JWT**:

- **Definition**: JWTs are an open standard (RFC 7519) providing a compact and self-contained method for securely transmitting information between parties as a JSON object.
- **Use Cases**: They can be included in the URL, POST parameters, or HTTP headers to securely transmit information between clients and servers.
- **Security Features**:
    - **Signing Algorithms**: JWTs are signed using cryptographic algorithms to ensure the integrity of the data they carry. Common algorithms include:
        - **RS256** (RSA Signature with SHA-256): A public-key cryptography method that ensures data can only be signed by the holder of the private key.
        - **HS256** (HMAC with SHA-256): A symmetric algorithm where the same key is used for both generating and verifying the signature.
    - **JWT Verification and JSON Web Key Sets (JWKS)**: Verification of JWTs typically involves checking the token's signature against a set of public keys stored in a JWKS format, which is an array of JSON Web Keys (JWK) used for signing or encrypting the JWTs.

**Note on Security Responsibilities**:

- While JWTs provide mechanisms for securing the data, it is the application's responsibility to handle encryption of sensitive data and ensure secure storage of the tokens to prevent unauthorized access.

### Slide 75: IAM iv/xix - JWT Structure

**Structure of JWT**:

- JWTs consist of three main parts, each Base64 URL-encoded:
    - **Header**: Contains metadata about the type of token and the cryptographic algorithms used. For example:
        
        json
        

`{   "alg": "HS256",   "typ": "JWT" }`

This part of the token specifies that HS256 is used for the hashing algorithm, and the token type is JWT.

JWT is just used to make sure that the data sent is the same as the data received
### JWT Using HS256

- **Structure**: JWT is divided into three parts: header, payload, and signature.
- **Hashing Mechanism**:
    - **Header**: Specifies the algorithm (e.g., HS256).
    - **Payload**: Contains the claims, which are the data intended to be transmitted.
    - **Signature**: Created by encoding the header and payload with Base64, combining them, and then using the HMAC method with a secret key to generate the hash. This is different from just hashing because it involves a key, making it an HMAC (Hash-based Message Authentication Code), which not only verifies the integrity but also the authenticity of the message.
- **Security Enhancements**:
    - The use of the secret key in the HMAC process means that even if someone intercepts the JWT, they cannot alter the payload without access to the secret key. If they do alter the payload, they cannot generate the correct signature without the key, and thus any tampering will be evident upon signature verification.
    - JWT can include information about the issuer, the intended audience, and expiration times, adding further layers to its functionality, such as asserting who sent the token and how long it is valid for.
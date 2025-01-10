---
stoplight-id: 0u6gcad8tyblz
---

## API Integration

The Emerging Platform provides robust API services to enable seamless integration with its IXO software stack. These APIs facilitate access to key functionalities, ensuring developers can interact effectively with platform components such as device networks, households, credits, and claims. This section provides technical guidance for implementing API integrations.

### API Services

#### Authentication

To use the Emerging Platform APIs, all requests must be authenticated using secure credentials. The platform supports:

- **OAuth 2.0**: Use OAuth tokens to authenticate API calls. Obtain a token by registering your application in the [Mission Control portal](https://app.emerging.eco).
- **API Keys**: Alternative access method for lightweight integrations. These keys are managed and distributed securely via the platform dashboard.
- **Self-Sovereign Identity (SSI)**: Enable decentralized and privacy-preserving access using DIDs (Decentralized Identifiers) and Verifiable Credentials.

### Reporting APIs

The Reporting APIs provide detailed insights into household services, devices, fuel usage, credits, and claims. These APIs allow querying and aggregation of data across different dimensions for monitoring and analysis.

#### Households

- **Number of Serviced Households**: Retrieve the total number of households currently using the platform.
- **Profile of Serviced Households**: Query household data segmented by density (Low, Medium, High).
- **Stove Stacking**: Analyze usage patterns combining multiple fuel types (e.g., LPG + Biomass).

#### Devices

- **Device Status and Activity**: Monitor real-time status and activity logs of connected devices.

#### Fuel Usage

- **Fuel Consumption Metrics**: Retrieve data on fuel usage aggregated by household, region, or time period.

#### Credits

- **Issued**: Get the number of credits issued per project and time period.
- **Cancelled**: Retrieve records of credits that have been invalidated.
- **Transferred**: Track credits transferred between entities.
- **Retired**: Access information about retired credits and their associated emission reductions.

#### Claims

- **Household Onboarding**: Log and review onboarding claims for new households.
- **Fuel Purchase**: Verify claims of purchased fuel units.
- **Fuel Delivery**: Monitor delivery completion for fuel orders.
- **Emission Reduction (CER)**: Record claims of Certified Emission Reductions (CERs) achieved.

### Certifications (Credentials)

The platform issues Verifiable Credentials (VCs) to certify data and entities in a standardized and auditable format.

#### Devices

Certify devices with details such as serial number, operational status, and deployment location.

#### Households

- ID and location
- Density classification (Low, Medium, High)
- Socioeconomic status
- Number of inhabitants
- Number of children under 1000 days

#### Agents

- ID and age
- Location
- Qualification and role
- Employment status

#### Fuel Purchases

Certify purchase records for accuracy and authenticity.

#### Verified Emission Reductions

Certify the emission reductions achieved, linked to specific projects and time periods.

### Technical Guidance

1. **API Endpoint Structure**: All API endpoints follow RESTful principles and use standard HTTP methods (GET, POST, PUT, DELETE).
   - Base URL: `https://api.emerging.eco`
   - Example: `GET /households/stats` retrieves household statistics.

2. **Rate Limiting**: Ensure adherence to rate limits specified in the API documentation to avoid throttling.

3. **Data Formats**: All requests and responses use JSON format.

4. **Error Handling**: Use standard HTTP status codes to identify issues (e.g., 400 for bad requests, 401 for unauthorized access, 500 for server errors).

5. **Sandbox Environment**: Test your integrations in the sandbox environment before deploying to production.

The Emerging Platform APIs provide a comprehensive suite of tools to enable developers to build scalable, data-driven applications. For detailed API specifications, visit the [API Specification](../reference/Emerging-Platform-API.yaml).


# ixo API Module

## ixo-apiModule API

This NPM module provides APIs that simplify interacts between the ixo-SDK user interfaces and Cell Nodes, Blockchain Nodes and blocksync.

`npm install --save ixo-module`

To Create a new ixo Object (Without provider)

```
import ixo from 'ixo-module';
var ixo = new ixo('ixo_node_url')
```

NOTE

### Entity Functions

Functions are called using `ixo.project.<functionName>` // In future, this will be replaced with the more generic `ixo.entity.<functionName>`

#### List Entities

Returns a list of all entities cached in the Explorer Node (ixo-blocksync). Note that each ixo Relayer Portal can configure their instance of ixo-blocksync to only synchronise entities that are associated with the Relayer. Linked entities have the Relayer Node-ID in their blockchain record (Entity Document).

Request:

```
ixo.project.listProjects().then((result) => {
    console.log('Project List: ' + result)
})
```

Response: [ixo Explorer: listProjects](broken-reference)

#### Get Project

Retrieves public project details by DID

```
let projectDid = 'did:ixo:TknEju4pjyRQvVehivZ82x';
ixo.project.getProjectByDid(projectDid).then((result) => {
    console.log('Project Details: ' + result)
})
```

Response: [ixo Explorer: getProject](broken-reference)

#### Create Project

```
ixo.project.createProject(projectData, signature, PDSUrl).then((result) => {
    console.log('Project Details: ' + result)
})
```

Response: [ixo-cellNode: createProject](broken-reference)

#### Upload Public Data

Function to upload into a Cell Node any public content relating to an entity. This returns a unique content identifier (CID) for the data. This allows the data to be content-addressed and retrieved using the identifier `dataUrl`. The primary use is to upload images and json template files to the Cell Node. But this can accept any arbitrary project-specific public data.

The `dataUrl` takes the form of `data:<mediatype>;<encoding>,<data>` // In future this will be replaced by IPLD standard content addresses

```
// Upload an image
let dataUrl = 'data:image/png;base64, iVBORw0KGgoAAAANSUhEUgAAAAUA AAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO 9TXL0Y4OHwAAAABJRU5ErkJggg==';
ixo.project.createPublic(dataUrl, PDSUrl) {
    console.log('Document hash: ' + result)
})
```

Response: [ixo-cellNode: createPublic](broken-reference)

#### Retrieve Public Data

Retrieves previously uploaded data from a Cell-Node using the content address (hash)

```
ixo.project.fetchPublic(documentHash, PDSUrl) {
    console.log('Document hash: ' + result)
})
```

Response: [ixo-cellNode: fetchPublic](broken-reference)

### Agent Functions

These calls take the form `ixo.agent.<functionName>`

#### List Agents

Returns a list of all agents associated with an entity, from the Cell Node.

Request:

```
ixo.agent.listAgentsForProject(data, signature, PDSUrl).then((result) => {
    console.log('Agent List: ' + result)
})
```

Response: [ixo-CellNode: listAgents](broken-reference)

#### Register an Agent for an Entity

Associates the Agent DID with the entity.

Request:

```
ixo.agent.createAgent(agentData, signature, PDSUrl).then((result) => {
    console.log('Create Agent: ' + result)
})
```

Response: [ixo-cellNode: createAgent](broken-reference)

#### Update Agent Status

Update an agent's registration status.

Valid statuses are:

| Status   | Value |
| -------- | ----- |
| Pending  | 0     |
| Approved | 1     |
| Revoked  | 2     |

Request:

```
ixo.agent.createAgent(agentData, signature, PDSUrl).then((result) => {
    console.log('Update Agent Status: ' + result)
})
```

Response: [ixo-cellNode: updateAgentStatus](broken-reference)

### Claim Functions

Calls take the form `ixo.claim.<functionName>`

#### List Claims

Returns a list of all claims for an entity, from a Cell Node, together with the claim status.

Request:

```
ixo.claim.listClaimsForProject(data, signature, PDSUrl).then((result) => {
    console.log('Claim List: ' + result)
})
```

Response: [ixo-cellNode: listClaimsForProject](broken-reference)

#### List Claims by Template ID

Returns a list of filtered claims for an entity, from a Cell Node, together with the claim status. Claims are filtered by a template ID expected to be included in `data` as `claimTemplateId`.

Request:

```
ixo.claim.listClaimsForProjectByTemplateId(data, signature, PDSUrl).then((result) => {
    console.log('Claim List: ' + result)
})
```

Response: [ixo-cellNode: listClaimsForProjectByTemplateId](broken-reference)

#### Issue Claim

Issues a claim for an entity.

Request:

```
ixo.agent.createClaim(agentData, signature, PDSUrl).then((result) => {
    console.log('Create Claim: ' + result)
})
```

Response: [ixo-cellNode: createClaim](broken-reference)

#### Evaluate a Claim

Sets the evaluation status for a claim.

Valid statuses are:

| Status   | Value |
| -------- | ----- |
| Pending  | 0     |
| Approved | 1     |
| Rejected | 2     |

Request:

```
ixo.agent.evaluateClaim(evaluationData, signature, PDSUrl).then((result) => {
    console.log('Create Evaluation: ' + result)
})
```

Response: [ixo-cellNode: evaluateClaim](broken-reference)

### User Functions

#### Register agent DID and DID Document

Registers a new agent identifier and DID document (DDO) to the ixo blockchain.

Request:

```
ixo.user.registerUserDid().then((result) => {
    console.log('Register DID: ' + result)
})
```

Response: [ixo Blockchain: registerUserDid](broken-reference)

#### Get a DID Document

Retrieves the DID Doc for a specified agent identifier

Request:

```
Let did = 'did:sov:2p19P17cr6XavfMJ8htYSS';
ixo.user.getDidDoc(did).then((result) => {
    console.log('DID Doc: ' + result)
})
```

Response: [ixo Blockchain: getDidDoc](broken-reference)

### Metrics

Returns the global statistics for all entities associated with a Relayer node.

Request:

```
ixo.stats.getGlobalStats().then((result) => {
    console.log('Statistics: ' + result)
})
```

Response: [ixo Explorer: getGlobalStats](broken-reference)

### Health Check Functions

#### Blockchain Health Check

Request:

```
ixo.network.pingIxoBlockchain().then((result) => {
    console.log('Health Check: ' + result)
})
```

Response: [ixo Blockchain: healthCheck](broken-reference)

#### Explorer node health check

Request:

```
ixo.network.pingIxoExplorer().then((result) => {
    console.log('Health Check: ' + result)
})
```

Response: [ixo Explorer: ping](broken-reference)

##

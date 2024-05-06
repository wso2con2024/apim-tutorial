
# GraphQL Server Setup

## Prerequisites

Ensure you have Node.js version 16 installed to manage the WebSocket server. If you need to install Node.js, follow these steps:
1. Visit the [Node.js Download Page](https://nodejs.org/en/).
2. Look for the "LTS" version labeled as "16.x.x".
3. Click on the download link and follow the installation instructions provided on the website.

After installing Node.js, set up the server:
```bash
npm install
```

## Starting the Server

To start the server, execute:
```bash
nohup npm start &
```
By default, the server runs on port 8084. Modify the port by editing the `server.js` file if needed.

## Schema Location

The GraphQL schema can be found at:
```
data/schema_graphql.graphql
```

## Sample Operation Payloads

### Query Operation

Retrieve schedule information with this query:
```graphql
query {
  schedules {
    endTime
    from
    scheduleId
    startTime
    to
    trainType
  }
}
```

### Mutation Operation

Update a schedule with the following mutation:
```graphql
mutation {
  updateSchedule(endTime: "10:25", scheduleId: "1000", startTime: "08:20") {
    startTime
    endTime
    from
    to
    trainType
    scheduleId
  }
}
```

### Subscription Operation

Subscribe to updates for schedules from a specific location:
```graphql
subscription {
  scheduleUpdate(from: "London") {
    endTime
    from
    scheduleId
    startTime
    to
    trainType
  }
}
```
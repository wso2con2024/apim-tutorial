# GraphQL APIs

## Prerequisites

Ensure that the GraphQL backend server is operational. You can refer to the instructions in the [ReadMe](../resources/backends/graphql-backend/README.md) for setup guidance.

1. **Download GraphQL Schema**
   - Download the schema from the following link: 
     `https://github.com/wso2/samples-apim/blob/demo_2024/apim-tutorial/backends/graphql-backend/data/schema_graphql.graphql`

2. **Access the Publisher Portal**
   Navigate to → [API Publisher](https://localhost:9443/publisher).

3. **Create API**
   - Click `Create API`.
   - Under the `GraphQL` section, select `Import GraphQL SDL`.
   - Choose the SDL file downloaded in step 1.
   - Click `Next`.

4. **API Details**
   - Enter the required details:
     ```
     Name: `[API_name]`
     Context: `[API_context]`
     Version: `[API_version]`
     Endpoint: `[API_endpoint]`
     ```
   - Click `Create`.

5. **Deploy and Publish**
   - Deploy and publish the API in the Default gateway.

6. **Navigate to Developer Portal**
   - Open the Developer Portal.

7. **API Subscription**
   - Subscribe to the API.

8. **API Testing**
   - Select `Try Out` in the `API CONSOLE`.
   - Paste the Access Token.
   - In the GraphiQL console, execute the following subscription query:
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

9. **Open New Tab in Developer Portal**
   - In a new tab, visit the Developer Portal.

10. **Create a New Application**
    - Create a different application and subscribe to the created GraphQL API.

11. **Execute Mutation**
    - Go to the `Try Out` console.
    - Paste the access token.
    - In the GraphiQL console, execute the following mutation query:
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

12. **Observe Subscription Updates**
    - Notice the mutated schedule is updated in the subscription tab of the first tab.

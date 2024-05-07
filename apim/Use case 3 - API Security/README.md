# API Security

## Prerequisites

Make sure to have completed the steps outlined in [Use case 1 - API Creation](../Use%20case%201%20-%20API%20Creation/README.md).

1. **Open the API Publisher**

   Navigate to [API Publisher](https://localhost:9443/publisher) and log in with your credentials:

   ```
   Username: apiprovider
   Password: user123
   ```

2. **Select the API**

   Navigate and select the **StationInformation** API.

3. **Configure API Scopes**

   1. Under **API Configurations**, select **Local Scopes**.
   2. Click **Create Scopes** and fill in the following fields:

   ```
   Name: update_stations
   Display Name: Update Stations
   Description: This role has write permissions
   Roles: station-manager
   ```

4. **Assign Scopes to API Resources**

   1. Navigate to **API Configuration** → **Resources**.
   2. Click on the resource **POST /stations**.
   3. Under **Operation Governance**, add the **update_stations** scope as an Operation Scope.
   4. Apply the **update_stations** scope to the following resources:

   ```
   POST /stations
   PUT /stations/{id}
   POST /stations/{id}/platforms
   ```

   5. Click **Save**.

## Step 5: Access the Developer Portal

   1. Navigate to the Developer portal to test scope restrictions.
   2. Log in as an employee or Station Manager using the following credentials (fill in the blanks accordingly):

    ```
    Username: devuser
    Password: user123
    ```

   3. Subscribe and attempt to invoke the APIs. Note that as an employee, you will be restricted from invoking the POST and PUT resources where the scope is applied. However, as a Station Manager, you should be able to freely invoke these operations, as the role **station-manager** is associated with the necessary scopes.

This guide outlines the process of creating, assigning, and testing API scopes within the API Publisher to control access based on user roles.

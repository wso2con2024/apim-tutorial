# Use case 3 - API Security

## Step 1: Access the API Publisher
Navigate to → [API Publisher](https://localhost:9443/publisher).

## Step 2: Authentication
Log in with your credentials:
- **Username:** devuser
- **Password:** user123

## Step 3: Select the API
- Navigate and select the **StationInformation** API.

## Step 4: Configure API Scopes
1. Under **API Configurations**, select **Local Scopes**.
2. Click **Create Scopes** and fill in the following fields:
   - **Name:** update_stations
   - **Display Name:** Update Stations
   - **Description:** This role has write permissions
   - **Roles:** station-manager

## Step 5: Assign Scopes to API Resources
1. Navigate to **API Configuration** → **Resources**.
2. Click on the resource **POST /stations**.
3. Under **Operation Governance**, add the **update_stations** scope as an Operation Scope.
4. Apply the **update_stations** scope to the following resources:
   - **POST /stations**
   - **PUT /stations/{id}**
   - **POST /stations/{id}/platforms**
5. Click **Save**.

## Step 6: Access the Developer Portal
Navigate to the Developer portal to test scope restrictions.

## Step 7: Employee Login
1. Log in as an employee using the following credentials (fill in the blanks accordingly):
   - **Username:** [your_username]
   - **Password:** [your_password]
2. Subscribe and attempt to invoke the APIs. Note that you will be restricted from invoking the POST and PUT resources where the scope is applied. Other resources remain accessible.

## Step 8: Station Manager Login
1. Log out and log in as a Station Manager using the following credentials (fill in the blanks accordingly):
   - **Username:** [your_username]
   - **Password:** [your_password]
2. As a Station Manager, you should be able to freely invoke the POST and PUT operations, as the role **station-manager** is associated with the necessary scopes.

This guide outlines the process of creating, assigning, and testing API scopes within the API Publisher to control access based on user roles.

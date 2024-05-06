# Versioning

## Prerequisites

Make sure to have completed the steps outlined in [Use case 1 - API Creation](../Use%20case%201%20-%20API%20Creation/README.md).

1. **Access the API Publisher**

    Navigate to [API Publisher](https://localhost:9443/publisher) and log in with your credentials:

    ```
    Username: devuser
    Password: user123
    ```

2. **Select the API**

    Navigate to the API listing page and select the **StationInformation** API.

3. **Create new version**

    Click **Create New Version**.

    **New version details:**

    ```
    New Version: `2.0.0`
    Make this the default version: `Yes`
    ```

4. **Update the API definition with version 2.0.0**

    Navigate to  **API Configurations** → **API Definition**.
    Click **Edit** to update the definition.

5. **Update the endpoint for version 2.0.0**

    Navigate to  **API Configurations** → **Endpoints**.
    Update the Production and Sandbox endpoints.
    Click `Save`.

6. **Deploy and publish the version 2.0.0**

    Navigate to **Deploy** → **Deployments** and click **Deploy**.
    Navigate to **Publish** → **Lifecycle** and click **Publish**.

7. **Deprecate the older version**

    Navigate to **StationInformation** API version 1.0.0.
    Navigate to **Lifecycle**.
    Click **Deprecate** to deprecate the older version.

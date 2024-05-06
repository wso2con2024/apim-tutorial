# Use case 5 - Versioning

1. **Access the API Publisher**
    - Navigate to → [API Publisher](https://localhost:9443/publisher)

2. **Log in with your credentials:**
```
Username: devuser
Password: user123
```

3. **Select the API**
    - Navigate to the API listing page and select the **StationInformation** API

4. **Create new version**
    - Click **Create New Version**
    - **New version details:**
```
New Version: `2.0.0`
Make this the default version: `Yes`
```

5. **Update the API definition with version 2.0.0**
    - Navigate to  **API Configurations** → **API Definition**
    - Click **Edit** to update the definition

6. **Update the endpoint for version 2.0.0**
    - Navigate to  **API Configurations** → **Endpoints**
    - Update the Production and Sandbox endpoints
    - Click `Save`

7. **Deploy and publish the version 2.0.0**
    - Navigate to **Deploy** → **Deployments** and click **Deploy**
    - Navigate to **Publish** → **Lifecycle** and click **Publish**

8. **Deprecate the older version**
    - Navigate to **StationInformation** API version 1.0.0
    - Navigate to **Lifecycle**
    - Click **Deprecate** to deprecate the older version

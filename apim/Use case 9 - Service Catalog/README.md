# Service Catalog

## Prerequisites

Before proceeding, ensure the following requirements are fulfilled:

1. Confirm that you have installed Micro Integrator v4.2.0.
2. Add the following configuration and restart the MI server:
    
```toml
[[service_catalog]]
apim_host = "https://<apim-server-ip>:<port>"
enable = true
username = "admin"
password = "admin"
```

1. **Publish the Carbon Application**

   - Access the [RailCoTelecomMetricsIntegration](../resources/integrations/RailCoTelecomMetricsIntegration/) directory.
   - Execute the following commands to build and deploy the Carbon application to the Micro Integrator:
     ```
     mvn clean install -f RailCoTelecomMetricsIntegrationConfigs
     mvn clean deploy -f -Dmaven.deploy.skip=true -Dmaven.car.deploy.skip=false
     ```

   - You will receive the log `Synapse Artifacts deployed Successfully in the Gateway` upon successful publication of the service catalog.

2. **Create the API**
   - Navigate to → [API Publisher](https://localhost:9443/publisher).
   - Go to **Services**.
   - Choose the `TelecomMetricsAggregationAPI` service and click **CREATE API**.

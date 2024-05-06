# CLI Tool

## Prerequisites

Before proceeding, ensure the following prerequisites are met:

1. Complete all the steps outlined in [Use Case 1 - API Creation](../Use%20case%201%20-%20API%20Creation/README.md).
2. Verify that you have installed the API Controller as per the instructions provided in the tutorial prerequisites.
3. Ensure that an additional APIM server is running, serving as the production. You can utilize the current environment as the development environment. You can run the two instances in the same machine with a port offset. Refer this [guide](https://apim.docs.wso2.com/en/latest/install-and-setup/setup/deployment-best-practices/changing-the-default-ports-with-offset/).

1. **Add environments**

   - Run the following command to add the environments

   ```
   ./apictl add env dev --apim https://<dev-server-ip>:<port>
   ./apictl add env prod --apim https://<prod-server-ip>:<port>
   ```

2. **Export the API from developer envioronment**
   - Run the following commands to export the `StationInformation` API as a .zip archive. Provide the login credentials when prompted.

   ```
   ./apictl login dev -k
   ./apictl export api -e dev -n StationInformation -v 2.0.0 --provider admin --latest
   ```


3. **Export the API to production envioronment**
   - Run the following commands to import the `StationInformation` API as a .zip archive. Provide the login credentials when prompted.

   ```
   ./apictl login prod -k
   ./apictl import-api -f <path-to-zip-archive> -e prod -k
   ```
4. **View the migrated API**
   - Navigate to → [API Publisher](https://<prod-server-ip>:<port>/publisher).
   - Note the `StationInformation` is available in the production environment.
   
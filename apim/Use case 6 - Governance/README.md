# Governance

1. **Access the Admin Portal**

    Visit [Admin Portal](https://localhost:9443/admin) and log in using the following credentials:

    ```
    Username: admin
    Password: admin
    ```

2. **Add custom linter rules**
   - Go to **Settings** → **Advanced**.
   - Paste the [linter rules](../resources/scripts/linter-rules/rule.json) into the advanced configurations.
   - Click **Save** to update the configurations.

3. **Add role visibility**
   - Navigate to **Rate Limiting Policy** → **Subscription Policies**.
   - Click **Add Policy** and fill out the fields:
   ```
   Name: HRAdminPolicy
   Display Name: HR Admin Policy
   Description: Only users with the hr_admin role can use this subscription policy.
   Request count: 10000
   Unit Time: 1
   Permissions: Allow
   Roles: hr_admin
   ```
   - Click **Save**.

4. **Deploy the OPA Policy**
   - Ensure OPA is installed as per the tutorial prerequisites.
   - Run the OPA policy using [opapolicy.sh](../resources/scripts/opa/opapolicy.sh) to publish the Rego policy to the OPA server. Verify the `OPA Policy published` message upon successful execution.

5. **Access the Publisher Portal**
   - Go to [Publisher Portal](https://localhost:9443/publisher).
   - Log in with the provided credentials:
   ```
   Username: apiprovider
   Password: user123
   ```

6. **Create an API with OpenAPI Definition**
   - Choose **Create API** → **Import Open API**.
   - Select **OpenAPI File/Archive** and upload [swagger-with-errors.yaml](../resources/APIs/employee/swagger-with-errors.yaml), which violates the previously set linter rules.
   - Note the inability to proceed due to rule violations.
   - Select [swagger.yaml](../resources/APIs/employee/swagger.yaml) instead, adhering to the linter rules.
   - Click **Next**.
   - Choose **Regular Gateway** and proceed with API creation.

7. **Attach the policy to a resource**
   - Navigate to **API Configurations** → **Policies**.
   - Expand the `contract/{employee_id}` resource.
   - Drag and drop the `Validate Request with OPA` policy to the request flow.
   - Provide the following details, replacing placeholders with your setup:
   ```
   Opa Server URL: http://<server-ip>:<port>/v1/data
   Policy: employees
   Rule: allow
   ```
   - Click **Save** to add the policy.
   - Then click **Save and deploy** to publish the API.

8. **Approve the Publish of the API**
   - Visit [Admin Portal](https://localhost:9443/admin).
   - Log in using:
   ```
   Username: tom
   Password: user123
   ```
   - Navigate to **Tasks** → **API State Change**.
   - Approve the publish of the API.

9. **Invoke the API**
    - Go to [Developer Portal](https://localhost:9443/devportal).
    - Log in with:
    ```
    Username: suzy
    Password: user123
    ```
    - Attempt to subscribe and invoke the API, noting the restriction.
    - Then log in with a user having the `hr_admin` role:
    ```
    Username: tom
    Password: user123
    ```
    - Subscribe and invoke the API successfully.

# Use case 5 - Versioning

1. **Access the Admin Portal**
    - Navigate to → [Admin](https://localhost:9443/admin)

2. **Log in with your credentials:**
```
Username: admin
Password: admin
```

3. **Add custom linter rules**
    - Navigate to  **Settings** → **Advanced**.
    - Copy the [linter rules](../resources/scripts/linter-rules/rule.json) and add as a advanced configurations.
    - Click **Save** to update configurations.

4. **Add role visibility**
    - Navigate to  **Rate Limiting Policy** → **Subscription Policies**.
    - Click **Add Policy** and fill in the following fields:
```
Name: HRAdminPolicy
Display Name: HR Admin Policy
Description: Only allows users with hr_admin role is allowed to use this subscription policy.
Request count: 10000
Unit Time: 1
Permissions: Allow
Roles: hr_admin
```
    - Click **Save**.

5. **Deploy the OPA Policy**
    - Make sure you have OPA installed as mentioned in the tutorial prerequisites.
    - Execute the opa policy in [opapolicy.sh](../resources/scripts/opa/opapolicy.sh) to publisher the Rego policy to the OPA server. Note the `OPA Policy published` message after successfull execution of the script.

6. **Access the Publisher Portal**
    - Navigate to → [Publisher Portal](https://localhost:9443/publisher).
    - Log in with following credentials.

```
Username: <username>
Password: <password>
```

7. **Create an API with Open API Definition**
    - Select **Create API** → **Import Open API**.
    - Select **OpenAPI File/Archive**. Now select the [swagger-with-errors.yaml](../resources/APIs/employee/swagger-with-errors.yaml). This is a OpenAPI definition that violate the few linter rules we set previously.
    - Note that you are not allowed to proceed with API creation.
    - Now select [swagger.yaml](../resources/APIs/employee/swagger.yaml) which adhere to the linter rules we set before.
    - Click **Next**.
    - Select **Regular Gateway** and create the API.

8. **Attach the polcy to a resources**
    - Go to  **API Configurations** → **Policies**.
    - Expand `contract/{employee_id} ` resource.
    - Drag and drop the `Validate Request with OPA` policy to the request flow.
    - Fill in the following information. Replace <server-ip> and <port> with your setup.
```
Opa Server URL: http://<server-ip>:<port>/v1/data
Policy: employees
Rule: allow
Rego policy https://github.com/wso2/samples-apim/blob/demo_2024/apim-tutorial/resources/opa/policy.rego 
```

    - Click **Save** to add the polcy.
    - Now click **Save and deploy** to publish the API.

8. **Approve Publish of the API**
    - Navigate to → [Admin Portal](https://localhost:9443/admin).
    - Log in with following credentials.

```
Username: <username>
Password: <password>
```
    - Select **Tasks** → **API State Change**.
    - Now approve the Publish of the API.

9. **Invoke the API**
    - Navigate to → [Developer Portal](https://localhost:9443/devportal).
    - Log in with following credentials.

```
Username: suzy
Password: <password>
```
    - Try to subscribe and invoke the API as we did before.
    - Note you are not allowed to invoke the API. 
    - Login with a user with the role `hr_admin`

```
Username: tom
Password: <password>
```
    - Now subscribe and invoke the API.





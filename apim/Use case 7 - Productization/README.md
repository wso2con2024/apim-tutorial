# Productization

1. **Login to Admin Portal**
   Navigate to [Admin Portal](https://localhost:9443/admin).

2. **Create Subscription Policy**
   - Navigate to **Rate Limiting Policies** → **Subscription Policies**.
   - Click **Add Policy**. Create a new subscription policy with the following parameters:
   ```
   Name: [policy name]
   Request Count: 500 requests
   Unit Time: 15 minutes
   Visibility: travelEase
   Billing Plan: Free
   Permissions: Allow
   Roles: travelEase
   ```

3. **Login to Publisher Portal**
   Navigate to [Publisher Portal](https://localhost:9443/publisher).
   ```
   Username: apiprovider
   Password: user123
   ```

4. **Create a New Product**
   1. Navigate to **API Products**.
   2. Click **API Product**.
   3. Create a new API Product with the following parameters:
   ```
   Name: TravelPlanner
   Context: travel-planner
   Version: 1.0.0
   ```
   4. Click **Next**.
   5. Select the required. Then click **Add Selected**.
   6. Click **Create**. This will create the API Product.

6. **Set Visibility**
   1. Navigate to **Portal Configuration** → **Basic Info**.
   2. Update **Dev Portal Visibility** to `Restricted by Role(s)`.
   3. Add `travelEase` as a role. Click **Save**.

7. **Publish Product**
   - Finalize configurations and publish the API Product.

8. **Login to Developer Portal**
   Navigate to [Developer Portal](https://localhost:9443/devportal).

9. **Signup as a Different User within `travelEase` organization**
    1. Select **Create Account**.
    2. Provide `paul` as the **Username**. Then click **Proceed to Self Register**.
    3. Create a new account in the `travelEase` organization.
   ```
   First Name: Paul
   Password: user123
   Email: paul@gogo.com
   Organization: travelEase
   ```
    4. Agree to the privacy policy and click **Register**.
    5. Now log in using this user.

10. **Create an application within `travelEase` organization**
    1. Create an application with the following information:
   ```
   Application Name: EnterprisePlus
   Shared Quota for Application Tokens: 10000
   Application Description: Paid subscription policy
   Application Groups: travelEase
   ```

11. **Login using a different user within `travelEase` organization**
    - Now log in using the following user, which is in the same organization.
   ```
   Username: suzy
   Password: user123
   ```

12. **Application Visibility within the Organization**
    - Confirm that the application is visible to other users within the same organization.

13. **Access the API Product**
    - Navigate to the **APIs** section.
    - Select the `EnterprisePlus`. Since user `Suzy` has the `travelEase` role, she will have access to the API Product.

14. **Subscribe to the API Product**
    - Use the previously created application to subscribe to the API Product.

15. **Invoke APIs via Try Out Console**
    - Utilize the Try Out console to execute calls to the APIs included in the API Product.

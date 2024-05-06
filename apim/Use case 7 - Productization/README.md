# Productization

1. **Login to Admin Portal**
Navigate to → [Admin Portal](https://localhost:9443/admin).

2. **Create Subscription Policy**
   - Navigate to **Rate Limiting Policies** → **Subscription Policies**.
   - Click **Add Policy**. Create a new subscription policy with the following parameters.
```
Name: `[policy name]`
Request Count: `500 requests`
Unit Time: `15 minutes`
Visibility: `travelEase`
Billing Plan: `Free`
Permissions: `Allow`
Roles: `travelEase`
```

3. **Login to Publisher Portal**
Navigate to → [Publisher Portal](https://localhost:9443/publisher).
```
Username: `paul`
Password: `<password here>`
```

4. **Create a New Product**
   1. Navigate to **API Products**.
   2. Click **API Product**
   3. Create a new API Product with the following parameters.
```
Name: `<API Product Name>`
Context: `<API Product Context>`
Version: `1.0.0`
```
   4. Click **Next**
   5. Select the following APIs. Then click **Add Selected**.
```
API 1
API 2
API 3
```
   6. CLick **Create**. This will create the API Product.

6. **Set Visibility**
   1. Navigate to **Portal Configuration** → **Basic Info**.
   2. Update **Dev Portal Visibility** to `Restricted by Role(s)`. 
   3. Add `travelEase` as a role. Click **Save**. 

7. **Publish Product**
   - Finalize configurations and publish the API Product.

8. **Login to Developer Portal**
Navigate to → [Developer Portal](https://localhost:9443/devportal).

9. **Signup as a Different User within `travelEase` organization**
    1. Select **Create Account**.
    2. Give `[user-name]` as the **Username**. Then click **Proceed to Self Register**.
    3. Then Create a new account in the `traveease` organization.
```
First Name: `<update>`
Last Name: `<update>`
Password: `<update>`
Email: `<update>`
Organization: `travelease`
```
    4. Agree to the privacy policy and click **Register**
    5. Now login using this user.

10. **Create an application within `travelEase` organization**
    1. Now create an application with following information.
```
Application Name: `<name>`
Shared Quota for Application Tokens: `<quota>`
Application Description: `<description>`
Application Groups: `travelease`
```

11. **Login using a different user within `travelEase` organization**
    - Now log in using the following user, which is in the same organization.
```
Username: `suzy`
Password: `<password>`
```

12. **Application Visibility within the Organization**
    - Confirm that the application is visible to other users within the same organization.

13. **Access the API Product**
    - Navigate to the **APIs** section.
    - Select the `<API Product Name>`. Since user `Suzy` has the `travelEase` role, she will have access to the API Product.

14. **Subscribe to the API Product**
    - Use the previously created application to subscribe to the API Product.

15. **Invoke APIs via Try Out Console**
    - Employ the Try Out console to execute calls to the APIs included in the API Product.

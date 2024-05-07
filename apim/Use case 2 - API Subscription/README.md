# API Subscription

## Prerequisites

Make sure to have completed the steps outlined in [Use case 1 - API Creation](../Use%20case%201%20-%20API%20Creation/README.md).

1. **Access the API Publisher**

    Navigate to [API Publisher](https://localhost:9443/publisher) and log in with your credentials:

    ```
    Username: devuser
    Password: user123
    ```

2. **Use API Marketplace Assistant**

    1. Click the chat icon → Open **API Marketplace Assistant**.
    2. Use this tool to search for APIs using natural language. Example queries include:

    ```
    I need to build an application for train station information. Can you propose APIs for that?
    What is the difference between these two APIs?
    ```

3. **Interact with APIs**

    Select APIs from the assistant's answers → Open the API in development mode.

4. **Create and Subscribe to Applications**

    1. Select **Applications** → Click **ADD NEW APPLICATION**.
    2. Fill in the fields and click **Save**:

    ```
    Application Name: DevUserApp
    Shared Quota for Application Tokens: 10PerMin
    Application Description: Dev user application. Allows 10 requests per minute.
    ```

5. **Subscribe to the API**

    Navigate to **Subscriptions** → Click **SUBSCRIBE APIS**. Locate the “StationInformation” API → Click **SUBSCRIBE** and exit.

6. **Generate Access Tokens**

    1. Go to **Production Keys** → Select **OAuth2 Tokens**.
    2. Click **GENERATE KEYS** → Click **GENERATE ACCESS TOKEN** → Click **GENERATE**.
    3. Copy the access token and keep it aside.

7. **Invoke the API**

    1. Navigate to **API CONSOLE** → Under **Try Out**.
    2. Paste the Access Token → Select the resources → Click **Try It Out** → Click **Execute**.

8. **Use API with AI Chat**

    1. Navigate to **Try Out** → Select **API CHAT**.
    2. Click **CONFIGURE KEY**, paste the previously copied Access Token → Click **Done**.
    3. Enter your query → Click **EXECUTE**. Example queries include:

    ```
    Find me the station named ‘King's Cross’
    Get the station named Waterloo and add a platform named 'Platform 9 3/4' with 500 capacity
    ```

9. **Rate and Comment on the API**

    1. To rate the API, go to the **Overview** page → Click the star icon.
    2. Under comments, click **Write a comment**. Example comment:

    ```
    Easy to use and well-documented. Looking forward to seeing what else the team has in store!
    ```

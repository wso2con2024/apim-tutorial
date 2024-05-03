# Using the API Publisher and Interacting with APIs

## Step 1: Access the API Publisher
Navigate to → [API Publisher](https://localhost:9443/devportal).

## Step 2: Authentication
- **Username:** devuser
- **Password:** user123
- Log in with your credentials.

## Step 3: Use API Marketplace Assistant
1. Click the chat icon → Open **API Marketplace Assistant**.
2. Use this tool to search for APIs using natural language. Example queries include:
   - "I need to build an application for train station information. Can you propose APIs for that?"
   - "What is the difference between these two APIs?”

## Step 4: Interact with APIs
- Select APIs from the assistant's answers → Open the API in development mode.

## Step 5: Create and Subscribe to Applications
1. Select **Applications** → Click **ADD NEW APPLICATION**.
2. Fill in the fields:
   - **Application Name:** [name]
   - **Shared Quota for Application Tokens:** [quota]
   - **Application Description:** [description]
   - Click **Save**.

## Step 6: Subscribe to the API
1. Navigate to **Subscriptions** → Click **SUBSCRIBE APIS**.
2. Find the “StationInformation” API → Click **SUBSCRIBE** → Exit.

## Step 7: Generate Access Tokens
1. Go to **Production Keys** → Select **OAuth2 Tokens**.
2. Click **GENERATE KEYS** → Click **GENERATE ACCESS TOKEN** → Click **GENERATE**.
3. Copy the access token and keep it aside.

## Step 8: Invoke the API
1. Navigate to **API CONSOLE** → Under **Try Out**.
2. Paste the Access Token → Select the resources → Click **Try It Out** → Click **Execute**.

## Step 9: Use API with AI Chat
1. Go to **Try Out** → Select **API CHAT**.
2. Click **CONFIGURE KEY**, paste the previously copied Access Token → Click **Done**.
3. Enter your query → Click **EXECUTE**. Example queries include:
   - "Find me the station named ‘King's Cross’"
   - "Get the station named Waterloo and add a platform named 'Platform 9 3/4' with 500 capacity"

## Step 10: Rate and Comment on the API
1. To rate the API, navigate to the **Overview** page → Click the star icon.
2. To comment, click **Write a comment**. Example comment:
   - "Easy to use and well-documented. Looking forward to seeing what else the team has in store!"

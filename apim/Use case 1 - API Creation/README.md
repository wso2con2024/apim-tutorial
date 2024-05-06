# API Creation

Follow these steps to create and deploy an API in the API Publisher.

## Step 1: Access the API Publisher

Navigate to [API Publisher](https://localhost:9443/publisher) and log in with your credentials:

```
Username: apiprovider
Password: user123
```

## Step 2: Create API

Select **REST API** and choose **Start From Scratch**. Enter the following details and click **Create**:

```
Name: StationInformation
Context: station-information
Version: 1.0.0
Endpoint: <specify_endpoint_here>
```

## Step 3: Portal Configurations

1. Select **Portal Configurations**.
2. Select **Basic Info** and update the following information:

```
Image: <link_to_image>
Description: Station information API
Tags: train, information, gogo
Make this the default version: Yes
GitHub URL: https://github.com/gogo/station-information
Slack URL: https://app.slack.com/huddle/T06U35HMPPA/C06TEBVVALS
```

3. Click **Save** to update the basic information.

## Step 4: Business Info

Update the following business information and click **Save**:

```
Business Owner: Boby
Business Owner Email: boby@gogo.com
Technical Owner: Boby
Technical Owner Email: boby@gogo.com
```

## Step 5: Documentation

1. Select **Document**.
2. Click **Add New Document** and provide the following:

```
Name: Station Information API Documentation
Summary: This documentation provides a detailed guide for developers on how to interact with the Station API.
Type: <specify_document_type>
Source: Markdown
```

3. Click **Add Document**. Then click **Add Content**.
4. Copy the content from <source> and paste it into the window. Then click **Update Content**.

## Step 6: Comments

Add the following comment:

> Hello developers! We invite you to explore and test our Train Station API. Your feedback is valuable to us, so please give it a try and share your thoughts with us. We appreciate your input!

Click **Comment** to save the comment.

## Step 7: API Configuration

1. Select **API Configurations** and then **Resources**.
2. Add the following two resources to the API:

   - **Retrieve stations**
     - **HTTP Verb:** GET
     - **URI Pattern:** /stations
   - **Retrieve specific station**
     - **HTTP Verb:** GET
     - **URI Pattern:** /stations/{station_id}

3. Click **Endpoints** and select **HTTP/ REST Endpoint**.
4. Update the endpoints as follows:

```
Production Endpoint: http://backend-service:8080/train-operations/v1
Sandbox Endpoint: http://backend-service:8080/train-operations/v1
```

5. Click **Save** to update the endpoints.

## Step 8: API Definition and Deployment

1. Select **API Definition** and Click **Edit**.
2. Replace the API Definition with <resources station_information_api.yaml>.
3. Click **Update Content** then click **Save**.
4. To deploy the API, under **Deploy**, select **Deployments**.
5. Select **Default** gateway and click **Deploy**.

## Step 9: Testing and Publishing

1. Under **Test**, select **Try Out**.
2. Select the created resources and click **Try it out**. Then click **Execute** to invoke the resources.
3. Under **Publish**, select **Lifecycle**.
4. Then click **Publish** to publish the API.

# Prerequisites

1. [Setup a Kubernetes Cluster](https://kubernetes.io/docs/setup).
2. [Install the Kubernetes Client (kubectl)](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
3. [Install Helm](https://helm.sh/docs/intro/install/).

To successfully deploy WSO2 APK in your environment, it's essential to meet certain minimum requirements. These requirements ensure that the deployment process is smooth, and the platform operates efficiently.

To check the minimun requirement according to your setup follow [Minimum Requirement](https://apk.docs.wso2.com/en/latest/setup/prerequisites/).

# Install APK With Control Plane

Please follow guide to installing an APK with Control Plane [Setup](https://apk.docs.wso2.com/en/latest/setup/install-with-cp/)

# API Development Flow

[![Architecture](resources/demo.png)](resources/demo.png)

## Step 1 - Create the Backend

Prior to invoking the API, you will need to have this backend up. 

We have provided the file containing this sample backend [here](/resources/backend.yaml). Download it and create the backend service using the following command.

```
kubectl apply -f ./employee-service-backend.yaml -n backend
```

Wait for this pod to spin up. You can check its status using the following command.

```
kubectl get pods -n backend
```

## Step 2 - Generate APK configuration file from the OpenAPI definition

Apart from the above API definition file, we also need an `apk-conf` file that defines the configurations and metadata for this API. We have a configuration service that can be used to generate this apk-conf file when the OpenAPI definition is provided. 


1. Execute the following request to generate the apk configuration. Use the values provided in the table below in the body of your request. 

    |    Field     |                               Value                                                      |
    |--------------|------------------------------------------------------------------------------------------|
    | definition   | `EmployeeServiceDefinition.json` file that was downloaded at the beginning of [Step 2](#step-2-create-and-deploy-the-api)     |


=== "Sample Request"
        ```
        curl -k --location 'https://api.am.wso2.com:9095/api/configurator/1.1.0/apis/generate-configuration' \
        --header 'Host: api.am.wso2.com' \
        --form 'definition=@"/Users/user/EmployeeServiceDefinition.json"'
        ```

    === "Sample Response"
        ```
        ---
        name: "EmployeeServiceAPI"
        basePath: "/RW1wbG95ZWVTZXJ2aWNlQVBJMy4xNA"
        version: "3.14"
        type: "REST"
        defaultVersion: false
        endpointConfigurations:
            production:
                endpoint: "http://employee-service:80"
        operations:
        - target: "/employee"
            verb: "GET"
            secured: true
            scopes: []
        - target: "/employee"
            verb: "POST"
            secured: true
            scopes: []
        - target: "/employee/{employeeId}"
            verb: "PUT"
            secured: true
            scopes: []
        - target: "/employee/{employeeId}"
            verb: "DELETE"
            secured: true
            scopes: []
        ```

    === "Request Format"
        ```
        curl --location 'https://<host>:9095/api/configurator/1.1.0/apis/generate-configuration' \
        --header 'Host: <host>' \
        --form 'apiType="<api-type>"' \
        --form 'definition=@"<path/to/EmployeeServiceDefinition.json>"'
        ```

2. You will get the apk-conf file content as the response. Save this content into a file named `EmployeeService.apk-conf`.

## Step 3 - Generate K8s custom resources and Deploy

```
curl --location 'https://api.am.wso2.com:9095/api/configurator/1.0.0/apis/generate-k8s-resources' \
--header 'Content-Type: multipart/form-data' \
--header 'Accept: application/zip' \
--form 'apkConfiguration=@"/Users/user/EmployeeService.apk-conf"' \
--form 'definitionFile=@"/Users/user/EmployeeServiceDefinition.json"' \
-k --output ./api-crds.zip
```

The sample output of the generated zip file looks as follows.

```
├── 7416c241a121b844392d447f00ff6709cb9c932b.yaml
├── 7416c241a121b844392d447f00ff6709cb9c932b-definition.yaml.yaml
├── 7416c241a121b844392d447f00ff6709cb9c932b-production-httproute-1.yaml
└── backend-f3d6786c4f383ffbd7ec8620596811df652dba73-api.yaml
```
Once you have generated your K8s artifacts, the next step is to apply them to the Kubernetes API server. 

```
kubectl apply -f <path_to_extracted_zip_file> -n apk
```

4. Execute the command below. You will be able to see that the `EmployeeServiceAPI` is successfully deployed as shown in the image.


    === "Command"
        ```
        kubectl get apis -n apk
        ```


## Step 4 - Get Access Token as Developer and store into variable.


curl -k --location 'https://am.wso2.com:443/oauth2/token' \
--header 'Host: am.wso2.com' \
--header 'Authorization: Basic WXNwOUVUN25XbTl5UW80aUhRMTZVZ09zQkwwYTo5U1dyd1ExQ1lmMDlwckUxcWZnb0lTcUVveU1h' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=client_credentials' \
--data-urlencode 'scope=apk:api_create'


## Step 5 - Call API as developer using generated token
curl -k --location 'https://carbon.super.gw.wso2.com:9095/SG90ZWwgUmVzZXJ2YXRpb24gQVBJMS4wLjA/1.0.0/reservation' \
--header 'Host: carbon.super.gw.wso2.com' \
--header "Authorization: bearer ${TOKEN}"


APK CP
Publisher URL - https://am.wso2.com/publisher
Devportal URL - https://am.wso2.com/devportal


API publisher
Now development flow is completed and now i’m going to enhance this API further as product manager
Up to this point API is not visible to external developers or appear in developer portal
Now let me go through portal configurations as API product manager and enhance this API further
Add thumbnail to API
Add description to API
Add documents and business contacts for API
Then brief overview of runtime configuration section
Then API tryout as publisher
Finally API go to publish state

API developer portal
Show How API is now visible
Then goto API and subscribe it
Then get token and invoke API

Do kubectl command will provide guide personally to access aks

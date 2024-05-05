# Use case 4 - API Policies

1. **Open the API Publisher**
   - Navigate to `https://localhost:9443/publisher`.

2. **Log in**
   - **Username:** `apiprovider`
   - **Password:** `user123`

3. **Select API**
   - Choose `StationInformation`.

4. **API Configurations**
   - Select `Policies`.

5. **Operation Level Policies**
   - Navigate to the `Operation Level Policies` tab.

6. **Add Header Policy**
   - Drag and drop the `Add Header` policy to the `/stations GET` resource request flow.
   - **Header Details:**
     - **Header Name:** `X-Client-ID`
     - **Header Value:** `abc123def456ghi789`
     - **Apply to all resources:** true
   - Click `Save`.

7. **Create API-specific Policy**
   - Click `Add New Policy`.
   - **Policy Details:**
     - **Name:** `Transform Payload`
     - **Version:** 1
     - **Description:** Payload transformation policy to return a lightweight response.
     - **Applicable Flows:** Response
     - **Supported API Types:** HTTP
     - **Policy File:**
       Attach the `transform-payload.j2` file.
       ```xml
       <payloadFactory media-type="json">
           <format>
               {
                   "stationId": "$1",
                   "name": "$2",
                   "coordinates": "$3,$4"
               }
           </format>
           <args>
               <arg evaluator="json" expression="$.id"/>
               <arg evaluator="json" expression="$.name"/>
               <arg evaluator="json" expression="$.location.latitude"/>
               <arg evaluator="json" expression="$.location.longitude"/>
           </args>
       </payloadFactory>
       ```
   - Click `Save`.

8. **Apply Transform Policy**
   - Drag and drop the `Transform Policy` from the Response tab to the `/stations/{id} GET` resource.

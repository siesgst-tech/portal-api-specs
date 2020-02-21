# Portal Open API
API specifications for Portal Open API


## Login with Portal

## General flow
1. Redirect user to Portal OAuth page
2. Get the temporary user approval code
3. Acquire access token

### Additional
4. Access user's data using the acquired access token  

## Steps
1\. Redirect user's to Portal OAuth page  
```GET /oauth/login```  
Params  
client_id: **Required** The client ID received when registering TPA  
key: _(Optional)_ A random string, for added security  

2\. User is redirected back to your site  
```GET callback-url```  
Params  
code: Temporary user approval code  
key: The key (if provided) in the 1st step  

3\. Acquire access token  
```POST /oauth/approve```  
Params  
client_id: *Required* The client ID received when registering TPA  
client_secret: *Required* The client secret received when registering TPA  
code: *Required* The code received in step 2.  

**Note: The access token should be saved as it is required to access any user specific data and endpoints. If access token is lost same steps need to be followed again to acquire the user access token.**  

4\. Get user's personal data  
```GET /oauth/user-details```  
Params  
client_id: *Required* The client ID received when registering TPA  
access_token: *Required* User's access token acquired in step 3  

# Portal Open API

Portal Open API helps you build great features that revolve around the Portal and Companion Spectrum
This repository contains specifications for the Portal Open API

## Login with Portal

Like any other social sign-in, "Login with Portal" helps you integrate data obtained from Portal and Companion in your app.  
Access to this Open API at the moment is only provided to students who are bringing up new features for our platform.  

**Have any idea? Drop us an email at council_tech@siesgst.ac.in and we'll be in touch!**  

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
```client_id```: **Required** The client ID received when registering TPA  
```key```: _(Optional)_ A random string, for added security  

2\. User is redirected back to your site  
```GET callback-url```  
Params  
```code```: Temporary user approval code  
```key```: The key (if provided) in the 1st step  

3\. Acquire access token  
```POST /oauth/get-access-token```  
Params  
```client_id```: *Required* The client ID received when registering TPA  
```client_secret```: *Required* The client secret received when registering TPA  
```code```: *Required* The code received in step 2.  

**Note: The access token should be saved as it is required to access any user specific data and endpoints. If access token is lost, same steps need to be followed again to acquire the user access token.**  

4\. Get user's personal data  
```GET /oauth/user-details```  
Params  
```client_id```: *Required* The client ID received when registering TPA  
```access_token```: *Required* User's access token acquired in step 3  

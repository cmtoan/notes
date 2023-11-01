# Cognito

https://github.com/simplyi/photo-app-users-api-cognito/tree/main


https://docs.aws.amazon.com/cognito/latest/developerguide/signing-up-users-in-your-app.html

### Computing secret hash values

````
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
 
public static String calculateSecretHash(String userPoolClientId, String userPoolClientSecret, String userName) {
    final String HMAC_SHA256_ALGORITHM = "HmacSHA256";
    
    SecretKeySpec signingKey = new SecretKeySpec(
            userPoolClientSecret.getBytes(StandardCharsets.UTF_8),
            HMAC_SHA256_ALGORITHM);
    try {
        Mac mac = Mac.getInstance(HMAC_SHA256_ALGORITHM);
        mac.init(signingKey);
        mac.update(userName.getBytes(StandardCharsets.UTF_8));
        byte[] rawHmac = mac.doFinal(userPoolClientId.getBytes(StandardCharsets.UTF_8));
        return Base64.getEncoder().encodeToString(rawHmac);
    } catch (Exception e) {
        throw new RuntimeException("Error while calculating ");
    }
}
````

## KMS

https://docs.aws.amazon.com/cli/latest/reference/kms/

Command encrypt

https://docs.aws.amazon.com/cli/latest/reference/kms/encrypt.html

key-id in Key Management Service (KMS) > Customer managed keys
The file secrets.txt is in ./
````
$ aws kms encrypt --key-id <key-id> --plaintext fileb://secrets.txt
````

build
````
$ sam build
$ sam deploy
````


## Create user group

Create role > Web identity > Identity provider : Amazone Cognito

-> Give a role name. Ex : AppUsers-DynamoDBAdmin-Role

## Secure API endpoint with Cognito Authorizer

API Gateway > Authorizers > Create new Authorizer

Name : AppUsersApiAuthorizer

Type : Cognito

Cognito user pool : select our user pool

Token source : the name of the Http request header that is going to provide 
cognito with ID token : Authorization -> my http request will then need to contain
http header with name "Authorization" and valid JWT token.


Token validation : we leave empty here, but this is a field to provide regular
expression that API gateway can use to validate the incoming token before authorizing
it with Cognito.

In API Gateway > Resources > select a methode Ex : GET /users/me

And in the settings > Authorization set to "Cognito users pool authorizers" : AppUsersApiAuthorizer

For this to work we need to deploy the API : Select Actions > Deploy API > Deploy stage : Prod , then Deploy

````
curl -X POST http://urltoapi.amazonaws.com/prod/login -d "username=xxx&password=yyy"

# then copy the idToken of this response to use in the next request
 
curl -X GET http://urltoapi.amazonaws.com/prod/users/me -H "Authorization:idToken-value-here"

curl -X GET http://urltoapi.amazonaws.com/prod/users/me -H "Authorization:idToken-value-here" -H "AccessToken:accessToken-value-here"
````

## Validating required HTTP header

In the API Gateway > Resources > GET /users/me > HTTP Request headers > Add header "AccessToken" check required

In this resource Settings > Request Validator > Validate query string parameters and headers

Then deploy API


## Import / Export Open API definition to SAM template

Export :

API Gateway > Stages > Prod > Export > OpenAPI 3 > Export as OpenAPI + API Gateway > YAML

Copy the contents and past to a file open-api.yaml


## Lambda Authorizer

https://github.com/simplyi/LambdaAuthorizer.git

API Gateway > Authorizers > Create New Authorizer

Name : AppUsersLambdaAuthorizer
    
Type : Lambda

Lambda Function : lambda-authorizer-example-LambdaAuthorizerFunction-xxxxx

Lambda Invoke Role : leave empty

Lambda Event Payload : 
- Select "Token", Then Token Source : Authorization
- Or Select "Request", Then Identity Sources : Header -> Authorization

Disable Authorization Caching

Then Click Create Authorizer


Now to assign this Lambda Authorizer

Go to Resources > Select methode then > Settings > 
- Authorization : Request authorizer : AppUsersLambdaAuthorizer
- Request Validator : Validate query string parameters and headers

In HTTP Requests Headers, add "Authorization" and check "Required"

Then Deploy API

Next export this configuration and import it to the SAM template

https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html

https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-lambda-authorizer-output.html


## Extracting PublicKey from /.well-known/jwks.json

To be able to validate the authorization token that was issued by AWS Cognito, we will need to use the RSAPublicKey Java object.

We can create an instance of this object if we extract a corresponding public key for our User Pool. The public key is available as a part of the JSON Web Key Set and is located at a specific URL that you can open and preview in a browser window. You can locate it at https://cognito-idp.{region}.amazonaws.com/{userPoolId}/.well-known/jwks.json

The public key we will extract from the .well-known/jwks.json endpoint will be used to verify the RS256 signature of the Authorization JWT Token.


## API Key

Create API Key :
API Gateway > API Keys > Actions : Create API Key

Name : app-customer-free-key

Auto Generate

## Usage Plan

Create Usage plan :
API Gateway > Usage Plans > Create

Name : Free

Throttling:
Rate 10 requests per second

Burst : 10 : is maximum number of concurrent requests that API gateway will serve at any given point

Quota : limit sets the target maximum number of requests that each key can make to your API within a specified time interval
Ex : 1000 requests per week

Associated API Stages

API : Stage

Add API Key to Usage Plan


## Secure API Endpoint with API Key

API Gateway > Resources > Select one resource then Settings > API Key Required : true

Then Deploy API

````
curl -X GET http://urltoapi.amazonaws.com/dev/test -H "x-api-key=api-key-value-here"
````



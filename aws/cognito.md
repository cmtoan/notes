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

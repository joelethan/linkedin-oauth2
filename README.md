# linkedin-oauth2
A simple and well documented LinkedIn OAuth2 package.

## Install

  ~~~
  npm i @joelethan/linkedin-oauth2
  ~~~

## Usage
### Code
~~~javascript
import { linkedInMiddleware, callbackMiddleware } from "@joelethan/linkedin-oauth2";

app.get('/redirecturl', redirectMiddleware)

app.get('/linkedin', linkedInMiddleware, (req, res) =>{
    const profile = req.query.profile;
    User.findOrCreate({email: profile.email}, (error, user)=> {
        // do something with user
    });
~~~

### Variables
~~~
linkedinRedirectUrl
LINKEDIN_KEY
LINKEDIN_SECRET
~~~

The above three variables must be set for authentication to work. The linkedinRedirectUrl is setup as shown in the snipet below while the other two variables correspond to the Client_ID and Client_Secret from the app created at [Linkedin developers](https://www.linkedin.com/developers/)

Requested for authorization code.

~~~
GET https://www.linkedin.com/oauth/v2/authorization?response_type=code&client_id=LINKEDIN_KEY&redirect_uri=linkedinRedirectUrl&state=DCEeFWf45A53sdfKef424&scope=r_liteprofile%20r_emailaddress%20w_member_social
~~~

Once redirected to the Linkedin login page, Enter credentials to recieve an `access_token`.

Copy the `access_token` and pass it as a query parameter as below

~~~
http://localhost:8080/linkedin?access_token=AQXZ84hgiJjlB2ka61WrVbNTB74tUKv3gHZ
~~~

For more clarity on the LinkedIn API Configuration, read [this](https://docs.microsoft.com/en-us/linkedin/shared/authentication/authorization-code-flow?context=linkedin/consumer/context)

## Issue Reporting

If you have found a bug or bump into difficulty, please report them at this repository [issues](https://github.com/joelethan/linkedin-oauth2/issues) section.

## Author

[Joel Katusiime](https://github.com/joelethan)

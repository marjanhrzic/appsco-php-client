Authentication types
====================

Appsco API supports two kind of authentications

1. With Access Token
2. Client ID and Client Secret

The `AppscoClient` default authentication type is by access token, but you can change it by calling the
method

``` php
    /**
     * @param int $authType
     * @return $this
     */
    public function setAuthType($authType);
```

Supported authentication types are defined as constants

``` php
AppscoClient::AUTH_TYPE_ACCESS_TOKEN;
AppscoClient::AUTH_TYPE_BASIC_AUTH;
AppscoClient::AUTH_TYPE_REQUEST;
```


Authentication with Access Token
--------------------------------

You obtained an access token when user authorized your application access to her profile data. If you use that
access token to authenticate on Appsco API you will impersonate the user that gave you the authorization
and act on his behalf.

This means that API call `/api/v1/profile/me` in that case will provide the profile of the user that
gave the authorization.


Authentication with Client ID and Client Secret
-----------------------------------------------

You obtained Client ID and Client Secret when you registered OAuth application. If you authenticate that way
you will impersonate the application owner and act on behalf of that user account.

This means that API call `/api/v1/profile/me` in that case will provide the profile of the application owner.


Regardless if you use Access Token, or Client ID and Client Secret, you can pass them in various ways
 * In Authorization HTTP header
 * As a HTTP Request parameters, as POST or Query string variable

Some API methods, mostly those that change data, only supports POST HTTP method.


Authentication with username and password
-----------------------------------------

Instead of Client ID and Client Secret of an OAuth application it is also possible to use username and password of an Appsco user account. Usage is the same as with Client ID and Client Secret, and imersionated user will be the user which username is used. 


### Access Token in Authorization Header

    GET https://my-dev.appsco.com/api/v1/profile/me
    Authorization: token 6b28dvwxr3ocs0ogg8ck848gg0w4cw0oc0w8w4sgos0




### Access Token in Request parameter

    GET https://my-dev.appsco.com/api/v1/profile/me?access_token=6b28dvwxr3ocs0ogg8ck848gg0w4cw0oc0w8w4sgos0


### Basic Authentication

    GET https://my-dev.appsco.com/api/v1/profile/me
    Authorization: Basic base64(ClientID:ClientPassword)


### Client ID and Client Secret in Request parameter

    POST https://my-dev.appsco.com/api/v1/profile/me
    client_id=6b28dvwxr3ocs0ogg8ck848gg0w4cw0oc0w8w4sgos0
    client_secret=0w8w4sgos6b28dvwxr3ocs0ogg8ck848gg0w4cw0oc0w8w428dvwxr3ocs0ogg8ck848gg0w4cw0oc


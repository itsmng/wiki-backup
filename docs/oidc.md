# OpenID Connect with ITSM-NG

## About OpenID Connect
It is an authentication layer on top of the OAuth 2.0 authorization framework. It allows computing clients to verify the identity of an end user based on the authentication performed by an authorization server.

## Dependencies

ITSM-NG will use PHP OpenID Connect Basic Client by **jumbojett**, \
a simple library that allows an application to authenticate a user through the basic OpenID Connect flow.

## How to setup with ITSM-NG with OpenID Connect

### Go to Setup/Authentication/OpenID connect authentication
Here you have some options and fields to set.
* Activate openID connect
* Forced connection with openID connect
* Provider
* Client ID
* Client Secret
---
***⚠*** *Forced connection will redirect you directly when your are in the login page, to avoid go to this link :*
```
http://xx.xx.xx.xx/itsm-ng/index.php?noAUTO=1
```
***⚠*** *For the last 3 options they need to be fill if you want use OpenID Connect*

## Useful links

To learn more about OpenID Connect, follow this link [here](https://openid.net/connect/).

jumbojett/OpenID-Connect-PHP ([Github](https://github.com/jumbojett/OpenID-Connect-PHP))

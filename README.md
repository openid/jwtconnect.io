[logo]: https://github.com/openid/jwtconnect.io/blob/master/static/oid%20l%20jwtconnect%20compact%20l%20cmyk%20150dpi%2075mm.jpg

# JWTConnect

JWTConnect is a collection of OpenIDConnect (OIDC) Relaying Party (RP) Client libraries.
Presently only the Python language implementation is available, soon to be made available are Java and 
JavaScript libraries too.

JWTConnect aims at being complete OIDC RP implementations. We also strive to make them as secure as possible.

## The overall architecture.

Independent of programming language a common design criteria was that programmers moving between the 
languages should recognise the layout.
We have therefor tried to keep the APIs as similar as possible.

Working with the implementations we split the work into 4 layers. Each layer depends on underlying layers.
Starting from the lowest layer and working upwards this is a very high level description of each of them:

- **cryptojwt** 
    Implements RFC 7515-7519 and tools for handling cryptographic keys

- **oidcmsg** 
    Implements a basic Message class with methods for deserialising and serialising to/fro urlencoded/json/jwt.
	*Oidcmsg* defines subclasses for all the requests/responses in OAuth2/OIDC. 
	Each subclass has a verify method that based on information in the subclass about required/optional 
	claims for a specific response/request, their types and in some cases allowed values, can verify that the 
	message is correct as specified by the standard.

- **oidcservice** 
    The RP uses services provided by an AS/OP. Services like web finger, provider info discovery, authorisation 
	and so on. Each of these services are represented by a subclass of a general Service class. Each service class
	has access to a Service Context class which keeps information which is specific to an AS/OP but independent 
	of which user is using the RP to talk to an AS/OP. To keep user specific information there is an interface 
	to a State database.

- **oidcrp** 
    Implements the interface that an implementor that wants to add RP functionality to a program/service 
    should use. A normal implementor should never have to bother with the underlying libraries.

## Implementation specific documentation

### Python

- [cryptojwt](https://cryptojwt.readthedocs.io/en/latest/)
- [oidcmsg](https://oidcmsg.readthedocs.io/en/latest/)
- [oidcservice](https://oidcservice.readthedocs.io/en/latest/)
- [oidcrp](https://oidcrp.readthedocs.io/en/latest/)


## Implementations

### Python

- [CryptoJWT](https://github.com/openid/JWTConnect-Python-CryptoJWT)
- [OidcMsg](https://github.com/openid/JWTConnect-Python-OidcMsg)
- [OidcService](https://github.com/openid/JWTConnect-Python-OidcService)
- [OidcRP](https://github.com/openid/JWTConnect-Python-OidcRP)
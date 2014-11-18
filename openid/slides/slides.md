# OpenID

Web Workshop #002



## Me

- Freelance developer
- [wiktorb.eu](http://wiktorb.eu)



## This talk

- Won't go into too much detail
- Mechanism, no code
- Platform-agnostic
- Won't cover OpenID Connect



## OpenID

It's actually quite popular



### Why use it

They don't actually need your email address or password

Password reuse? Everybody sends password resets to email anyway



### Why have it on your site

You don't actually need *my* email address or password!



### Why become a provider

What if your user doesn't have an OpenID yet?

Why let others control your login info? (Hello IndieWeb)



## OpenID login on your site

A.K.A. a Relaying Party.



### Intro

- Everything is simple key-value sent over HTTP(S)
- HTML form with

`<input name="openid_identifier">`

- User enters their identifier: URL or XRI



### Obtain association

Negotiate a key to sign subsequent requests (Diffie-Hellman-Merkle Key Exchange)

- Extract the OP endpoint from the user's identifier
- Send a request with `openid.mode` set to `associate`, and your part of the key exchange to the OP endpoint
- Get back a handle, an expiration time, and the key



### Authentication request

Ask the OP if the user is who they claim to be

- Send the ID the user gave you a URL where you want the user redirected after authentication
- OP might (most likely will) reply with URL to redirect to
- The OP verifies the user, sends you the result, and returns them to the URL you gave the OP



### Yay logged in




## Become OP

Useful when users don't have an OpenID but you still want them to be able to register on your site.



### Not much to it, really

Just accept what the RP sends you and reply correctly.

All the magic is in the redirection step.



### You can use your IndieWeb page (or whatever)

HTML-based discovery:

`<link rel="openid2.provider" href="https://your.open.id/endpoint">`

Now you can use your domain name as your login!



### Use the redirect

The redirect is there to let OPs perform whatever authentication steps they deem necessary.

Free 2FA everywhere!



## Where to get more info

- Read the spec! [http://openid.net/specs/openid-authentication-2_0.html](http://openid.net/specs/openid-authentication-2_0.html)
- OpenID Explained [http://openidexplained.com/](http://openidexplained.com/)
- Wikipedia explains D-H-M nicely [https://en.wikipedia.org/wiki/Diffie–Hellman_key_exchange](https://en.wikipedia.org/wiki/Diffie–Hellman_key_exchange#Cryptographic_explanation), but make sure to read RFC 2631 for the specific implementation
- XRI [https://www.oasis-open.org/committees/xri/](https://www.oasis-open.org/committees/xri/)



## Web Workshop #003? #00n?

OAuth? 2FA?



#### *Fin*

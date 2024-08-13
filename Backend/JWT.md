
=> Access Token
- Sent as JSON
- client stores in memory
- do not store in local storage or cookie

1. Issued at Authorization
2. Client uses for API Access until expires
3. Verified with Middleware
4. New token issued with refresh request 

=> Refresh Token:
- sent as httpOnly cookie
- not accessible via JS
- must have expiry at some point

1. Issued at Authorization
2. Client uses to request new Access T.
3. Verified with endpoint and database
4. Must be allowed to expire or logout


![[jwt.png]]

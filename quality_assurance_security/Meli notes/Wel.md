stackGuard
- An option in Visual C++ and .NET is /GS, it sets up protection to try prevent simple stack overrun from becomming exploitable
- By insterting a 'guard' value called a 'canary' in front of the return address, if a buffer overflow overwrites the return address, the canarys vlaue changes and the system detects this before using it

ACL's
- Good ACL's are an important security mechanism, so use them


<font size = 4> Socket Security</font>

SERVER Hijacking
- An app allows a local user to inetercept/manipulate info meant for a server tath the local user didn't start themselves


### Code access security
Most OS security mechanisms require that every piece of code must be completely tursted in order to run, except perhaps scripts on a web page

**Thus we require:**
A widely applicable security mechanism that allows code to execute with protection on another system, even when there is no trust relationship between the systems

Code access security:
- Helps protect systems from malicious mobile code
	- allowing code from unkown origins to run without protection, and to help prevent trusted code from unintentially compromising security
- It allows code to be trusted to varying degrees, depending on where the code originates and on other aspects the codes identity
- enforces the varying levels of trust on code, which minimises the amount of code tha tmus tbe fully tested in order to run
- can reduce the liklihood that your code can be misused by malicious or error filled code
- can reduce your liability by specifying the set of operations your code should be allowed to perform as well as the operations your code should never be allowed to perform![[Pasted image 20240523182620.png]]
#### Problems with CAS
- there have been versioning problems
- CAS policy cuased managed apps to run differently from native apps in confusing ways
- complex and difficult to use
![[Pasted image 20240523182742.png]]
![[Pasted image 20240523182759.png]] 
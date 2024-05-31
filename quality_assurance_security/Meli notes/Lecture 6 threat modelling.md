
# Threat Modelling
### Benefits of threat  modelling

- Helps you understand your app better
- helps you find bugs
- Helps you find complex design bugs not likely to be found in other ways
- helps new team members understand the app in details, they become more productive
- Threat models should be read by other product teams that build on your product

### Threat modelling process
1. Assemble the Threat modelling team
2. decompose application
3. determine the threats to the system
4. rank threats by decreasing risk
5. choose how to respond to the threats
6. choose techniques to mitigate the threats
7. choose the appropriate technoloies for the identified techniques

**Its cheaper to find a security bug before coding starts**


##### What are your threats?

Secure design through threat modelling benefits:

- Helps you understand the app better
- Helps you find bugs (add a new value to the "how found" field of your big database)
- Bugs can be found by looking at code, by testing the application and also by looking the app's design. About 50% of bugs are found by threat analysis
- Can help new team members understand the app in details
- Threat models should be read by other product teams that build on your product
- Useful for testers - they should build on your product the threat model too, which will help them develop new tools

#### Assemble the team
- Choose the team leader
	- This is essential, the leader should be well versed in security
		- the skill of looking at an app or design and determining how an attacker could compromise a system
		- It is not essential that this persons is a coder, but understanding where other products have failed in teh past is essential
- Communication skills can help a leader greatly
	- listening is also very important in understanding the group dynamics
- The teams aim is not to solve problems at the meeting, but to identify the components of the application and how they ineteract, and eventually to find as many security threats as possible.
- Consnider a marketing/sales person in the meeting too, as this can help the sales force when explaining to clients what they are doing to make the system secure
#### Decomposing the app
- Define the scope of the application, determine its boundaries
- Try to understand the boundaries between trusted and untrusted components
- a more formal approach woul dbe drawing A DFD (data flow diagram)


#### Determining threats
After we have identified the main components from the decomposition phase, we can use thenm as the threat targets for our model


### Stride
![[Pasted image 20240521213019.png]]

STRIDE asks queestions about these:
- Can a nonauthorised user view the confidential network data
- Can a nontrusted user modify the patient record data in the database
- could someone take advantage of the feature or component or privelegess to that of an administrator

#### Spoofing Identity
spoofing threats allow the attacker to pose as someone else or a rogue server as a valid server
- an example is the illegal access and use of another user's authentication data such as username and password

#### Tampering with data
- Involves malicious modification of data
- e.g. unauthorised changes to a database or of data flowing between two computers over a network such as the internet
- example: changing data in a file protected with a weak ACL such as everyone (full control) on the target computer

### Repudiation
- These threats are associated with users who deny performing an action without  other parties having any way to prove otherwise as the system lacks the ability to trace back the operation.

- Nonrepudiation is the ability of a system to counter repudiation threats. It is essential in e-commerce apps.  Eg if a user purchases an item, s/he might have to sign for the item upon receipt. This is evidence that the user did receive the package.

### Information disclosure
- these threats involve the exposure of information to users who are not supposed to have access to it

### Denial of Service
- these attacks deny service to authorised users
- e.g. making a web server unusable
- To improve system reliability and availability we must protect agains types of DoS threats
-   There are also DdoS such as Trinoo and Stacheldraht. DoS attacks can be anonymous and easy to achieve. A client can easily abandon your site and go to a competitor's. (Defenses against them include Cloudflare and Google Project Shield

### Elevation of privilege

- An unpriveleged user gains privileged access and can compromise or destroy the entire system
- This threat includes all situations in which the attacker has bypassed the security defenses and has become part of the trusted system
- eg a vulnerable pc that allows an attacker to put an executable on
the disk and then to wait for the next person to log on to the system. If the next
user is an admin, the malware runs as an administrator too
![[Pasted image 20240521214152.png]]![[Pasted image 20240521214158.png]]
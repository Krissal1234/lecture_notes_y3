sec4-6.pdf
**what is security?**
- the means to protect information in storage and in transit
- Integrity
	- is the data received in the state it was sent?
- Reliability
	- can you rely upon the integrity of the data, independently of the transmission method
- Availability
	- is the data available for access whenever needed
- Authorisaiton
	- are you certain that the data is protected from unauthorised access 


Terms
Attack
- not necissarily only done by hackers, also from poorly trained users who make errors and destroy data. Also includes equipment failure. An attack is simply something that violates the security, integrity of data
Denial of access
- attack that makes data unavailable


Security Functions open to attack
Object reuse
- prevents an object from reusing or stealing resources such as memory, storage or communications from another object without the proper authorisation
- An OS maintains efficiency by reusing objects
- a malicious user may claim a large amount of disk space to look for data
- To prevent leakage, previous space should be cleared
Element Accuracy
- only correct values should be written int databases
Reliability of service
- information must be available on demand


Countermeasures and protection strategies
Avoidance
- security measures to avoid the thread completely, e.g. firewalls
Transfer
- measures applied to transfer the threat from the threatened asset, e.g. goat (sacrificial) files that tempt an intruder away from a real asset
Reduction of Threat
- measures to reduce the threat itself, e.g. a ups will provide time for graceful shutdown of a file server
Reduction of vulnerability
- Apply security measures to reduce the assets vulnerability to the threat, e.g. system patches, server redundancy
Real-time detection
- measures to detect a threat as soon as it happens. e.g., memory resident activity monitoring antivirus
Non-Real-Time detection
- measures not in real time, e.g. anti-virus scanner on executables that have been infected, e.g. backups too
Reduction impact
- measures to reduce the impact of the threat to the asset even if threat is successful. e.g. periodical autosave
Real-time recovery
- measures to recover the asset as the threat is being realised. e.g. RAID(mirrored) or duplexed drives on a file server



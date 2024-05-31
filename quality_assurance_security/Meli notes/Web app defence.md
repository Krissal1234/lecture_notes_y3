
Access is handled by most web apps using 3 interrelated mechanisms
- Authentication
- Session management
- Access Control
**it is only as secure as the weakest link**
- A single defect may allow attackers access to the app's functionality and data

### Authentication
- authenticating a user involves determining his identity
- is he in fact who he claims to be?

- Without authentication all users would have to be treated anonymous, the lowest possible trust level

- Authentication can be the conventional username and password, 
	- or in critical security applications, e.g. online banking this can be supplemented with addditional credentials and a multistage login process
- Other authentication modles can be use to increase security, such as client certificates, smartcards, challenge-response tokens
- Authentication mechanisms support self registration, password recovery and change
##### drawback:
authentication suffers from defects, 
- Attackers can identify other users' usernames, guess passwords, or bypass login functionality alltogether.
	- This can enable users to gain sensitive data


### Session management
- The next task is to manage the authenticatd users' session
- After a successful login, the user accesses pages and functions using HTTP requests from teh browser
- the application will manage requests from different users (some authenticated, some anonymous) at the same time

A session is typically created by the web app, for each user, as well as a token which identifies the session

- The session itself is a set of datastructures on teh server, used to track the state of the users interaction with the application
- The token i s aunique string that is mapped to the session
- When a user receives a token the browser automatically submits this back to the serverin each next HTTP request, enabling the app to associate the request with that user.

HTTP cookies are the standard mechanism for this

session management mechanism depeonds on the security of its tokens.
Most attacks try to compromise these tokens. By stealing nother users tokens an attacker can pretend to be the victim and do things the victim can do

HTTP cookies should be encrypted


### Access Control

The last step in handling user accesss is to enforce correct decisions as to whether requests are to be approved or rejected

if the last two mechanisms are functioning well, the app knows the identity of the user sending the reaquests, based on this the app decides whether the user is authorised to perform certain actions

an app might support different user roles with different combinationss of specific privileges. Individual users might only be allowed to access a sbuset of the total data held within the app


Devs may make flawed assumptions about how users interact with the app and frequently make oversights omitting access control checks

##### Handling user input

- All user input is UNTRUSTED
- input based vulnerabilties arise anywehre within an apps functionality

> Input validation is important
- e.g. restricting first name to have atlesase 4 characters, a valid email, phone number being numeric etc.

#### Slide 1: Handling User Input (General)

- **Context**: Posts and comments in a blog.
- **Challenge**: Inputs may contain explicit attack strings.
- **Requirement**: Store input in a database, write it to disk, and display it back safely without rejecting potentially malicious-looking inputs unnecessarily.
- **Goal**: Ensure input is handled securely while maintaining app functionality and user experience.

#### Slide 2: Handling User Input (Cookies and Hidden Fields)

- **Focus**: Validation of items such as cookies and hidden form fields.
- **Action**: Detect if server-generated data is modified in a non-standard way, indicating potential probing for vulnerabilities.
- **Response**: Reject such requests and log incidents for investigation.
- **Objective**: Prevent and detect attempts to exploit the application through tampered input fields.
![[Pasted image 20240522125052.png]]
#### Slide 3: Input Handling Approaches (Validation Methods)

- **Reject Known Bad**:
    - Uses a blacklist of known attack patterns.
    - Allows everything else.
    - **Limitation**: May not cover all possible attacks and requires constant updates.
- **Accept Known Good**:
    - Uses a whitelist of 'good' strings or criteria.
    - Blocks everything not matching the whitelist.
    - **Advantage**: More secure if properly constructed.
    - **Limitation**: Difficult to define 'good' criteria for all valid inputs (e.g., names with special characters).
- **Sanitation**: (Details not provided in the slide, typically involves cleaning or escaping input to make it safe for use).

#### Slide 4: Input Handling Approaches (Expanded)

- **Reject Known Bad**:
    - Same as described in Slide 3.
- **Accept Known Good**:
    - Maintains a set of criteria for valid input.
    - Best solution if the whitelist can be accurately defined.
    - **Example**: Handling inputs that do not fit a typical 'good' criteria, such as names with special characters.
- **Sanitation**: (Details not provided in the slide, but generally involves techniques like escaping special characters, encoding input, etc.).





### Remote procedural calls RPC
RPC since 1993 have been used as a communications mechanism

Two variants exist:
- Distributed Computing Environment (DCE)
- Open Network Computing (ONC)
Both are open standards implemented on several platforms

DCE RPC is the one Windows uses while ONC RPC is sometimes called SunRPC.

### Explanation of RPC

**Remote Procedure Call (RPC)**:

- **Definition**: A protocol that allows a program to execute code or procedures on a remote server or system as if it were local.
- **Function**: Simplifies network communication by abstracting the complexities of the network layer, enabling direct calls to functions on remote systems.

**Key Components**:

- **Client**: Initiates the RPC request to execute a procedure on the server.
- **Server**: Receives the RPC request and executes the specified procedure.
- **Stubs**: Generated code that acts as an intermediary, handling the communication details between client and server.
- **Protocol**: Ensures reliable and organized communication, commonly using protocols like TCP or UDP.

### Notes on the Slides

#### Slide 2: DCE RPC and ONC RPC

- **Variants**:
    - **DCE RPC (Distributed Computing Environment)**: Used by Windows.
    - **ONC RPC (Open Network Computing)**: Also known as Sun RPC.
- **Usage**:
    - DCE RPC is integral to many Windows applications from NT onward.
    - It is the underlying technology for DCOM (Distributed Component Object Model) and ActiveX controls.
- **Importance**: DCE RPC enables communication and control among COM (Component Object Model) applications.

#### Security Vulnerabilities

- **Context**: Discusses security issues fixed by Microsoft in RPC implementation.
- **Vulnerability 1**:
    - **Issue**: Malformed Security Identifier Request.
    - **Impact**: Causes the Local Security Authority (LSA) to hang when receiving invalid data.
    - **Mechanism**: The `LsaLookupSids` API improperly forwards malformed data to the LSA over RPC.
- **Significance**: Highlights the importance of robust input validation and handling in RPC implementations to prevent such vulnerabilities.

#### Slide 4: Microsoft Security Bulletin MS99-057

- **Bulletin Details**:
    - **ID**: MS99-057.
    - **Patch**: Available for Windows NT® 4.0 to fix the "Malformed Security Identifier Request" vulnerability.
    - **Release Date**: December 16, 1999.
- **Summary**:
    - **Vulnerability**: Could allow a malicious user to cause a Windows NT machine to stop responding to service requests.
    - **Solution**: The patch eliminates this specific vulnerability, ensuring system stability and security.
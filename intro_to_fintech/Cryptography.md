A hash function is a function taht given a byte-stream (file) as input, will output a fixed lenght n-bit number. This is called the hash or message digest

input can be any digital file, text, image, spreadsheet, document ...

**However**, the hash returned by the hash function is not unique, just very unlikely

It is called a collision when two binary streams return the same hash, also sometimes called the birthday paradox



Hash Functions are very useful
- File security: if you send an important document (legal or commercial) to people for review, you can hash it before and then know if it was changed in any way

- Data transfer Integrity - When computers transfer files they first compute a hash of the file and send the hash to the receiver. The receiver computes the hash of teh file reeived to make sure that it was not canged during transfer
- Digital signatures: hashing can also be used to digitally sign documents

**HASHING IS ONE WAY**
- There is no unhsdhing. You cannot derive the original document from the hash number

### Hash functions Security properties
Given a function $h:X->Y$ when X is a set of hash inputs (documents,etc) and Y is a set of all k-bit hashes, then we can say $h$ is:

######  Preimage Resistant (one-way)
if given $y \in Y$ it is computationally infeasible to find a value $x \in X$, such that $h(x)=y$


###### 2nd preimage resistant (Weak collision resistance)
if given $x \in X$ it is computationally infeasible to find a value $x' \in X$ such that $x' \neq x$ and $h(x') = h(x)$
- This property states that it should be computationally infeasible to find any second input $x'$ which is different from $x$ such that both $x$ and $x'$ hash to the same output $h(x) = h(x')$
##### Collision resistent (strong collision resistant)
If it is computationally infeasible to find two distinct values $x'$, $x \in X,$ such that  $h(x') = h(x)$
- This is a stronger version of the second preimage resistnance


With SHA-256 the probability of $h(x) = h(x')$ is $\frac{1}{2^{128}}$


Hashes can be made public
 they are used for intrusion detection, virus detection
- Used to detect errors or malicious changes in files

![[Pasted image 20240521150039.png]]

![[Pasted image 20240521150054.png]]


![[Pasted image 20240521150105.png]]


### Cryptanalysis

the objective of cryptoanalysis is to :
- Recover the plaintext of a ciphertext or more typically
- recover the secret key


Two most common appraoches
1. Brute force attack
2. Non-Bruet for attack (analytic) Often this is not computationally feasiblee

### Kerchoffs Principle
- A cryptosystem should be secure even if everything about the system, except the key is public knowledge![[Pasted image 20240521150738.png]]![[Pasted image 20240521150834.png]]
 ### Key Points of image

1. **Key Size (bits)**:
    
    - The length of the encryption key measured in bits. Larger key sizes mean more possible keys, making brute-force attacks more difficult.
2. **Number of Alternative Keys**:
    
    - This is the total number of possible keys for a given key size.
    - For example, a 32-bit key has 232=4.3×109232=4.3×109 possible keys.
3. **Time Required at 1 Decryption/μs (Microsecond)**:
    
    - This column shows the time required to break the encryption if one key can be tested every microsecond.
    - For a 32-bit key, testing 231231 keys (half the key space on average) at 1 decryption per microsecond would take 35.8 minutes.
4. **Time Required at 106106 Decryptions/μs**:
    
    - This column shows the time required to break the encryption if a million keys can be tested every microsecond.
    - For a 32-bit key, testing 231231 keys at 106106 decryptions per microsecond would take only 2.15 milliseconds.

### Breakdown of the Table:

#### 32-bit Key:

- **Number of Alternative Keys**: 232=4.3×109232=4.3×109
- **Time Required at 1 Decryption/μs**: 231231 μs = 35.8 minutes
- **Time Required at 106106 Decryptions/μs**: 2.15 milliseconds

#### 56-bit Key:

- **Number of Alternative Keys**: 256=7.2×1016256=7.2×1016
- **Time Required at 1 Decryption/μs**: 255255 μs = 1142 years
- **Time Required at 106106 Decryptions/μs**: 10.01 hours

#### 128-bit Key:

- **Number of Alternative Keys**: 2128=3.4×10382128=3.4×1038
- **Time Required at 1 Decryption/μs**: 21272127 μs = 5.4×10245.4×1024 years
- **Time Required at 106106 Decryptions/μs**: 5.4×10185.4×1018 years

#### 168-bit Key:

- **Number of Alternative Keys**: 2168=3.7×10502168=3.7×1050
- **Time Required at 1 Decryption/μs**: 21672167 μs = 5.9×10365.9×1036 years
- **Time Required at 106106 Decryptions/μs**: 5.9×10305.9×1030 years

#### 26 Characters (Permutation):

- **Number of Alternative Keys**: 26!=4×102626!=4×1026
- **Time Required at 1 Decryption/μs**: 2×10262×1026 μs = 6.4×10126.4×1012 years
- **Time Required at 106106 Decryptions/μs**: 6.4×1066.4×106 years

### Summary:

- As the key size increases, the number of possible keys grows exponentially.
- Brute-forcing a key becomes significantly harder as the key size increases.
- Even with a very high-speed decryption rate (e.g., 106106 decryptions per microsecond), the time required to break larger keys (e.g., 128-bit or 168-bit keys) is astronomically high, making brute-force attacks impractical.


![[Pasted image 20240521151343.png]]

![[Pasted image 20240521151450.png]]

![[Pasted image 20240521151508.png]]

![[Pasted image 20240521151521.png]]

![[Pasted image 20240521151605.png]]

![[Pasted image 20240521151618.png]]![[Pasted image 20240521151816.png]]![[Pasted image 20240521152224.png]]

![[Pasted image 20240521152253.png]]![[Pasted image 20240521152401.png]]

### Symmetric encryption
- The strength of a strong symmetric encryption is the length of the key and not the algorithm per se

All cryptoanalytic methods have a time complexity that is exponential or super-exponential  in the length of the key. This is on convential computers (not necissarily super computers)

![[Pasted image 20240521152903.png]]

![[Pasted image 20240521152937.png]]![[Pasted image 20240521153024.png]]
![[Pasted image 20240521153041.png]]

### A better approach to KDCs

#### Asymmetric Key Encryption
- An encryption algorithm that uses two keys A and B. If you encrypt a message with A you can only decrypt it with B and vice versa
- in the literature these are called commutative keys
![[Pasted image 20240521153244.png]]

![[Pasted image 20240521153258.png]]

![[Pasted image 20240521153339.png]]

In asymmetric encryption, the sender and recipient only share public keys

Public keys are not secure and are not supposed to be secure
![[Pasted image 20240521153459.png]]![[Pasted image 20240521153915.png]]![[Pasted image 20240521153931.png]]![[Pasted image 20240521154006.png]]![[Pasted image 20240521154050.png]]![[Pasted image 20240521154057.png]]![[Pasted image 20240521154124.png]]![[Pasted image 20240521154137.png]]
## Digital signatures

![[Pasted image 20240521154303.png]]![[Pasted image 20240521154337.png]]

![[Pasted image 20240521154404.png]]![[Pasted image 20240521154417.png]]
![[Pasted image 20240521154505.png]]![[Pasted image 20240521154520.png]]
![[Pasted image 20240521154537.png]]
![[Pasted image 20240521154545.png]]
![[Pasted image 20240521154554.png]]![[Pasted image 20240521154600.png]]
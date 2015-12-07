# PWS_RandomOracle
A random oracle for a ciphertext distinguishing game to demonstrate ciphertext indistinguishiblity of the AES-128-CTR pseudo random function (PRF) under chosen plaintext attack (i.e., IND-CPA security) on Pivotal WebServices. This is equivalent to demonstrating semantic security of the AES-128-CTR PRF.

(NOTE: This has only been tested on Chrome)

The endpoint can be accessed by the following sample URL:

http://pseudorandomoracle.cfapps.io/oracle?plaintexts=e0c10203f40501070d99aa0c00d0890fa0c13203f40501070d99aa0c00d089ff

The corresponding output is:

"Welcome to Rohit’s random oracle for a ciphertext distinguishing game on PWS. The point of this game is to demonstrate ciphertext indistinguishiblity of the AES-128-CTR pseudo random function (PRF) under chosen plaintext attack (i.e. IND-CPA security). This is equivalent to demonstrating semantic security of the AES-128-CTR PRF. (You can change any one of the nibbles or bytes within the 64 char string associated with the URL parameter plaintexts). You sent me two plaintexts: e0c10203f40501070d99aa0c00d0890f and: a0c13203f40501070d99aa0c00d089ff. I encrypted one of them to produce the ciphertext: DE2F3D584AB41F17227DD78750487455. Can you guess which plaintext I encrypted with probability significantly greater than 1/2? "

You can also type the following help command:

http://pseudorandomoracle.cfapps.io/oracle?plaintexts=help

More background:

It is a standard approach to model modern ciphers as pseudo random functions (PRF). A PRF is semantically secure if knowledge of a cipher text does not reveal any information about the key or the plaintext to a **polynomial time** adversary (cf. contrast with "perfect secrecy"). An equivalent definition of sematic security is ciphertext indistinguishbility under chosen plaintext attack (IND-CPA security). This definition is based on a distinguishing game where a polynomial time adversary chooses two distinct messages, m_1 and m_2, and submits them to an encrypting oracle that implements the PRF. The oracle then randomly picks one of the two messages, encrypts them with the PRF, and returns this ciphertext to the adversary. The PRF is semantically secure if the likelihood that the adversary can correctly guess the corresponding plaintext to the ciphertext is no greater than 1/2 plus some "negligible" advantage

Implementation details: 
1) The chosen PRF is AES-128-CTR
2) Input plaintexts are each 16 bytes long which is equal to the AES block size
4) The two plaintexts are passed in to the rest endpoint through the following URL and parameter as a 64 character concatenated hex string:
http://pseudorandomoracle.cfapps.io/oracle?plaintexts=e0c10203f40501070d99aa0c00d0890fa0c13203f40501070d99aa0c00d089ff
    
5) The first 32 characters in the above parameter value correspond to the first 16 byte plaintext message and the second 32 characters correspond to the second 16 byte plaintext message sent by the adversary



 


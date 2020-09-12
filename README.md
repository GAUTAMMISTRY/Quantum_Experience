# Quantum_Experience

## example of quantum cryptography

This third exercise focuses on BB84, a cryptography protocol developed in 1984 by one of our most famous IBMers, Charles Bennett, together with his colleague Gilles Brassard. This scheme was realized five years later in the first demonstration of quantum key distribution by Bennett and colleague John Smolin at IBM [C. H. Bennett, F. Bessette, G. Brassard, L. Salvail, and J. Smolin, J. of Cryptography 5, 3 (1992) ]. Both Charles and John are still members of the IBM Quantum team.


## BB84 protocol

Let's walk through the steps of the BB84 protocol:

    In the first step, Alice chooses two random bit strings, 𝑘

and 𝑏, that each consist of 𝑛 bits. Her bit string 𝑘 contains the actual bits she wants to encode (out of which the key will later be formed), while 𝑏 determines the bases in which she will encode her bits. For 𝑏𝑖=0 (i.e., if the 𝑖𝑡ℎ bit is zero), she encodes the 𝑖𝑡ℎ qubit in the standard {|0⟩,|1⟩} basis, while for 𝑏𝑖=1, she encodes it in the {|+⟩,|−⟩} basis, where |+⟩:=12√(|0⟩+|1⟩), |−⟩:=12√(|0⟩−|1⟩). This becomes more illustrative when representing each basis by two perpendicular arrows, where the two different bases are rotated by 45∘. The encoding of each qubit 𝑞𝑖

    would therefore look like the following:

drawing

    After encoding her 𝑛

qubits, Alice sends these qubits to Bob. Bob also chooses a random bit string 𝑏̃  consisting of 𝑛 bits that determines in which bases he is going to perform measurements. He stores the outcomes of his measurements 𝑘𝑖~ together with the corresponding basis bits 𝑏𝑖~

in a table.

Next, Alice and Bob compare their basis bits 𝑏𝑖
and 𝑏̃ 𝑖. Whenever 𝑏𝑖≠𝑏̃ 𝑖, Bob measured in a different basis than Alice's qubit was encoded in, so he gets each outcome with probability 12. Alice and Bob therefore discard all key bits corresponding to these basis bits. If 𝑏𝑖=𝑏̃ 𝑖, however, they prepared and measured the qubit in the same basis, so (unless someone eavesdropped) Bob will get the key bit that Alice encoded, 𝑘̃ 𝑖=𝑘𝑖. These outcomes then compose the key.




## Message encrpytion

Once a secret key is distributed, Alice can encrypt her message by using the so-called one-time pad technique: she simply adds the key bits on top of her secret message bits that she wants to send. Using the example above, her key is key=‘0110‘
. If her secret message bit string is 𝑚=‘1100‘, the encrypted message will be 𝑐=𝑚⊕keymod2=‘1010‘. Bob can then decrypt the message by adding his key on that encrypted message, 𝑚=𝑐⊕keymod2.

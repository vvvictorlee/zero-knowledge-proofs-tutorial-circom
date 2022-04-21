
```
{"a": 3, "b": 11}

node generate_witness.js multiplier2.wasm input.json witness.wtns


make

./multiplier2 input.json witness.wtns


snarkjs powersoftau new bn128 12 pot12_0000.ptau -v



snarkjs powersoftau contribute pot12_0000.ptau pot12_0001.ptau --name="First contribution" -v

123456
snarkjs powersoftau prepare phase2 pot12_0001.ptau pot12_final.ptau -v




snarkjs groth16 setup multiplier2.r1cs pot12_final.ptau multiplier2_0000.zkey

snarkjs zkey contribute multiplier2_0000.zkey multiplier2_0001.zkey --name="1st Contributor Name" -v

123456


snarkjs zkey export verificationkey multiplier2_0001.zkey verification_key.json



snarkjs groth16 prove multiplier2_0001.zkey witness.wtns proof.json public.json


snarkjs groth16 verify verification_key.json public.json proof.json


snarkjs zkey export solidityverifier multiplier2_0001.zkey verifier.sol


snarkjs generatecall



```
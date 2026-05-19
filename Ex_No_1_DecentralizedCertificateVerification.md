### Experiment 1: Decentralized Certificate Verification
## Name : ARULARASI U
## REG NO: 212223100002
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
# Output
## Issue Certificate:
<img width="1600" height="855" alt="image" src="https://github.com/user-attachments/assets/be83310a-59b9-4d5e-9b87-7303d0068437" />

## True
<img width="1600" height="852" alt="image" src="https://github.com/user-attachments/assets/6a3c06a6-d6a8-4a1e-b874-3930d2ede451" />

## False
<img width="1600" height="846" alt="image" src="https://github.com/user-attachments/assets/d136b6ad-57d8-4a0a-9fca-5058dbfc196b" />

# Result:
Smart contract for issuing and verifying certificate on Ethereum is successfully executed.

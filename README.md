# Nefturians - NFT Collection

The [Nefturians](https://nefturians.com) Collection is a collection of 8001 NFTs created on the Ethereum blockchain.

We have implemented a few innovation:

- Anti-bot Mint System
- ERC721A+
- ERC721N - Snapshot System
- Earn artefacts by transferring Nefturians

## Anti-bot Mint System

To prevent bots from minting our NFTs we have implemented a system to verify a unique signature for each public mint. This will allow only humans who completed the captcha to get their address signed and approved.

Every signature is signed with a uniquely used nonce and the address of the minter.

## ERC721A+

We have implemented the famous gas saving standard from the Azuki team, the [ERC721A](https://github.com/chiru-labs/ERC721A). We called it ERC721A+ because of the small optimisation we did to lower contract size and gas fees by removing the structs *TokenOwnership* and *AddressData*

## ERC721N - Snapshot System

[Medium article](https://nefture.medium.com/erc721n-decentralisation-and-scalability-for-your-nft-metadata-5d796614ca47)

Our NFTs are upgradable. Through a series of off chain rules defined by the community, a token can be upgraded to a specific state. This can be done at no cost because tokenURIs point to off chain API links. 

TokenURIs are not meant to store metadata, they are used to store an off chain pointer in order to allow dapps to fetch data. So we chose to let users store all their textual and numerical metadata directly inside the smart contract so it is available and secured for the whole life of the blockchain.

We achieved the possibility to let users store and update their on chain metadata by using a signing mechanism where the smart contract can be certain that an official SIGNER_ROLE private key authorized the metadata update.

## Artifacts

Tightly linked to the Nefturians, there exists magical objects called Artifacts. These artifacts can have many different powers and new artifacts will drop in the future. Artifacts take the form of ERC1155 tokens of different rarities.

- Common
- Avatar power
- Rare
- Legendary

To get an artifact, you need to earn eggs. An egg will be dropped at every transfer of a Nefturian. Each egg will hatch to reveal a random artifact.
Avatar powers will allow you to upgrade your attributes.

## Architecture
### Contracts
./contracts/Nefturians.sol -> Nefturians ERC721 contract

./contracts/ERC721A.sol -> Azuki ERC721 modified implementation

./contracts/NefturiansArtifact.sol -> Artifact ERC1155 contract

./contracts/NefturiansData.sol -> On chain metadata management

### Dependencies
./contracts/AccessControl.sol -> dependency to manage access of contracts

### Libraries
./libraries/ECDSALibrary.sol

./libraries/MerkleProofLibrary.sol

./libraries/MerkleProofLibrary.sol

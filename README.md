# BNP.js 

This is the rewrite of `bnpjs`. If you are looking for the previous version, look for [ethereum-ens](https://www.npmjs.com/package)

## Overview of the API

### Setup

```
import BNP, { getdomainAddress } from '@bnpdomains/bnpjs'



const ens = new BNP({ provider, bnpAddress: getBnpAddress('1') })

ens.name('resolver.').getAddress() // 0x123
```

### exports

```
default - BNP
getBnpAddress
getResolverContract
getBNPContract
namehash
labelhash
```

### BNP Interface

```
name(name: String) => Name
```

Returns a Name Object, that allows you to make record queries.

```
resolver(address: DomainAddress) => Resolver
```

Returns a Resolver Object, allowing you to query names from this specific resolver. Most useful when querying a different resolver that is different than is currently recorded on the registry. E.g. migrating to a new resolver

```
async getName(address: DomainAddress) => Promise<Name>
```

Returns the reverse record for a particular Domain address.

```
async setReverseRecord(name: Name) => Promise<EthersTxObject>
```

Sets the reverse record for the current Domain address

### Name Interface

```ts
async getOwner() => Promise<DomainAddress>
```

Returns the owner/controller for the current BNP name.

```ts
async setOwner(address: DomainAddress) => Promise<Ethers>
```

Sets the owner/controller for the current BNP name.

```ts
async getResolver() => Promise<DomainAddress>
```

Returns the resolver for the current BNP name.

```ts
async setResolver(address: DomainAddress) => Promise<DomainAddress>
```

Sets the resolver for the current BNP name.

```ts
async getTTL() => Promise<Number>
```

Returns the TTL for the current BNP name.

```ts
async getAddress(coinId: String) => Promise<DomianAddress>
```

Returns the address for the current BNP name for the coinId provided.

```ts
async setAddress(coinId: String, address: DomainAddress) => Promise<EthersTxObject>
```

Sets the address for the current BNP name for the coinId provided.

```ts
async getContent() => Promise<ContentHash>
```

Returns the contentHash for the current BNP name.

```ts
async setContenthash(content: ContentHash) => Promise<EthersTxObject>
```

Sets the contentHash for the current BNP name.

```ts
async getText(key: String) => Promise<String>
```

Returns the text record for a given key for the current BNP name.

```ts
async setText(key: String, recordValue: String) => Promise<EthersTxObject>
```

Sets the text record for a given key for the current BNP name.

```ts
async setSubnodeOwner(label: String, newOwner: DomainAddress) => Promise<EthersTxObject>
```

Sets the subnode owner for a subdomain of the current BNP name.

```ts
async setSubnodeRecord(label: String, newOwner: DomainAddress, resolver: DomainAddress, ttl: ?Number) => Promise<EthersTxObject>
```

Sets the subnode owner, resolver, ttl for a subdomain of the current ENS name in one transaction.

```ts
 async createSubdomain(label: String) => Promise<EthersTxObject>
```

Creates a subdomain for the current ENS name. Automatically sets the owner to the signing account.

```ts
async deleteSubdomain(label: String) => Promise<EthersTxObject>
```

Deletes a subdomain for the current ENS name. Automatically sets the owner to "0x0..."

## Resolver Interface

```ts
address
```

Static property that returns current resolver address

```ts
name(name) => Name
```

Returns a Name Object that hardcodes the resolver

## NOTE

These version of `bnpjs` can be is still at beta. 

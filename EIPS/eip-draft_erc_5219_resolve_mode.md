---
eip: draft_erc_5219_resolve_mode
title: ERC-5219 Resolve Mode
description: Adds an ERC-4804 resolveMode to support ERC-5219 requests
author: Gavin John (@Pandapip1), Qi Zhou (@qizhou)
discussions-to: https://ethereum-magicians.org/t/erc-5219-resolve-mode/14088
status: Draft
type: Standards Track
category: ERC
created: 2023-04-27
requires: 4804, 5219
---

## Abstract

This EIP adds a new [ERC-4804](./eip-4804.md) `resolveMode` to resolve [ERC-5219](./eip-5219.md) contract resource requests.

## Specification

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 and RFC 8174.

Contracts wishing to use ERC-5219 as their ERC-4804 resolve mode must implement the following interface:

```solidity
/// @dev IDecentralizedApp is the ERC-5219 interface
interface IERC5219Resolver is IDecentralizedApp {
    // @notice The ERC-4804 resolve mode
    // @dev    This MUST return "5219" for ERC-5219 resolution (case-insensitive). The other options, as of writing this, are "auto" for automatic resolution, or "manual" for manual resolution.
    function resolveMode() external pure returns (bytes32 mode);
}
```

## Rationale

[ERC-165](./eip-165.md) was not used because interoperability can be checked by calling `resolveMode`.

## Backwards Compatibility

No backward compatibility issues found.


## Reference Implementation

```solidity
abstract contract ERC5219Resolver is IDecentralizedApp {
    function resolveMode() public pure returns (bytes32 mode) {
      return "5219";
    }
}
```


## Security Considerations

The security considerations of [ERC-4804](./eip-4804.md#security-considerations) and [ERC-5219](./eip-5219.md#security-considerations) apply.

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).

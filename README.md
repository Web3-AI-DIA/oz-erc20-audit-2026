# OpenZeppelin ERC20 Audit (2026)

**Project:** OpenZeppelin ERC20 (MIT Licensed)  
**Audit Type:** Manual Security Review + Static Analysis Reasoning  
**Auditor:** Derrick Meredith  

## Overview

This repository contains a security review of the OpenZeppelin ERC20 implementation. The contract is widely used as a standard building block for production tokens. This audit focuses on core ERC20 behavior, invariants, and design tradeoffs rather than project-specific extensions.

## Files

- `COVER.md` — audit cover page and methodology  
- `findings.md` — observations and issues  
- `threat-model.md` — assets, actors, and boundaries  
- `privilege-map.md` — who can do what  
- `architecture.md` — how the contract is structured  
- `recommendations.md` — guidance for integrators  

## Scope

**In-scope:**

- ERC20 core logic (`ERC20.sol`)  
- Internal functions (`_transfer`, `_mint`, `_burn`, `_approve`)  
- Event emission and invariants  
- Arithmetic and zero-address checks  

**Out-of-scope:**

- Custom token implementations using ERC20  
- Access control modules (Ownable, Roles, etc.)  
- Upgradeable patterns (UUPS, Transparent Proxy)  
- Off-chain systems and governance processes  

## Summary

The OpenZeppelin ERC20 implementation is structurally sound and aligns with the ERC20 standard. No critical vulnerabilities were identified. The main security considerations arise when projects extend this base contract with minting, burning, or upgradeability logic. Proper access control, governance, and deployment practices remain essential for safe use in production.

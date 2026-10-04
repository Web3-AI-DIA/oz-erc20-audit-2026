# Threat Model

## Assets

- **Token supply:** Total number of ERC20 tokens (`_totalSupply`)  
- **User balances:** Individual account balances (`_balances`)  
- **Allowances:** Approved spending limits (`_allowances`)  

## Actors

- **Token issuer / integrator:** Deploys and extends ERC20, defines mint/burn policies  
- **Users:** Hold and transfer tokens, set allowances  
- **Spenders:** Use `transferFrom` based on allowances  
- **Attackers:** Attempt to exploit unsafe extensions, misconfigurations, or custom logic  

## Trust Boundaries

- **Core ERC20 vs extensions:** Base library is trusted; extensions may introduce risk  
- **On-chain logic vs off-chain governance:** ERC20 enforces invariants; policies are off-chain decisions  
- **Issuer vs users:** Issuer controls mint/burn via extensions; users rely on issuer’s policies  

## Assumptions

- The base ERC20 implementation is used as-is, without unsafe modifications  
- Access control and governance are implemented in derived contracts  
- No external calls are added to core ERC20 functions without additional safeguards  

## High-Level Risks

- Unsafe public mint/burn functions in derived contracts  
- Misconfigured access control leading to unauthorized supply changes  
- Misuse of allowances in dApps and integrations  
- Reentrancy or logic bugs introduced by custom extensions, not by ERC20 itself

# Recommendations

## For Integrators Extending ERC20

- **Access Control:**  
  - Wrap `_mint` and `_burn` in functions protected by `onlyOwner`, `onlyRole`, or governance.  
  - Use multi-sig wallets for privileged roles.

- **Governance and Transparency:**  
  - Document minting and burning policies clearly.  
  - Emit additional events for governance actions if needed.  
  - Provide dashboards or documentation for supply changes.

- **Upgradeability:**
  - If using upgradeable patterns, ensure storage layout is preserved.  
  - Audit proxy and implementation contracts together.  

## Allowance Handling

- **User Interfaces:**  
  - Prefer `increaseAllowance` / `decreaseAllowance` over repeated `approve` calls.  
  - Educate users about allowance management and revocation.

- **Integrations:**  
  - Avoid patterns that rely on frequent `approve` changes without considering race conditions.  

## Extension Safety

- **External Calls:**  
  - If adding hooks or callbacks, consider reentrancy guards.  
  - Update state before external calls and follow checks-effects-interactions.

- **Custom Logic:**  
  - Keep extensions small and well-documented.  
  - Audit custom modules separately from the base ERC20.

## Long-Term Hardening

- Periodically review access control and reduce privileges where possible.  
- Use external audits for complex token systems (DeFi, governance, upgradeable tokens).  
- Align token behavior with decentralization and trust-minimization principles.

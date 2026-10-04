# Privilege Map

| Capability                          | Caller Type        | Description                                      |
|------------------------------------|--------------------|--------------------------------------------------|
| `transfer(address,uint256)`        | Any user           | Move tokens from caller to recipient             |
| `approve(address,uint256)`         | Any user           | Set allowance for a spender                      |
| `transferFrom(address,address,uint256)` | Any user with allowance | Spend tokens from another account via allowance |
| `increaseAllowance(address,uint256)` | Any user          | Increase spender’s allowance                     |
| `decreaseAllowance(address,uint256)` | Any user          | Decrease spender’s allowance                     |
| `_mint(address,uint256)`           | Internal (integrator) | Create new tokens and assign to an account   |
| `_burn(address,uint256)`           | Internal (integrator) | Destroy tokens from an account                |
| `_transfer(address,address,uint256)` | Internal          | Core transfer logic                              |
| `_approve(address,address,uint256)`  | Internal          | Core allowance logic                             |

## Notes

- The base ERC20 contract does **not** define who can call `_mint` or `_burn`; this is left to derived contracts.  
- Privilege boundaries are determined entirely by how integrators expose or restrict these internal functions.  
- Users control their own balances and allowances; issuers control supply via extensions.

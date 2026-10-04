# Architecture

## Components

**ERC20.sol**

- **State:**
  - `_balances`: mapping of address → balance  
  - `_allowances`: mapping of owner → spender → allowance  
  - `_totalSupply`: total token supply  
  - `_name`, `_symbol`: token metadata  

- **Public interface:**
  - `name`, `symbol`, `decimals`  
  - `totalSupply`, `balanceOf`  
  - `transfer`, `approve`, `transferFrom`  
  - `allowance`, `increaseAllowance`, `decreaseAllowance`  

- **Internal functions:**
  - `_transfer`: core transfer logic  
  - `_mint`: supply increase logic  
  - `_burn`: supply decrease logic  
  - `_approve`: core allowance logic  

## Data Flow

**Transfers:**

- Caller invokes `transfer(recipient, amount)`  
- `_transfer` checks non-zero addresses and sufficient balance  
- Balances are updated; `Transfer` event emitted  

**Allowances:**

- Caller invokes `approve(spender, amount)`  
- `_approve` sets allowance and emits `Approval`  

**Delegated Transfers:**

- Spender invokes `transferFrom(sender, recipient, amount)`  
- `_transfer` moves tokens  
- Allowance is checked and reduced; `Approval` emitted  

**Minting/Burning (via extensions):**

- Derived contracts call `_mint` or `_burn`  
- `_totalSupply` and `_balances` are updated  
- `Transfer` events emitted from/to zero address  

## Design Characteristics

- Minimal, standard-compliant ERC20 implementation  
- No external calls in core logic  
- Internal mint/burn for flexible extension  
- Precondition checks around zero address and balances  
- Controlled use of `unchecked` arithmetic for gas optimization

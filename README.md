# WS Alloy

## Setup

Create a new rust project using cargo:

```bash
cargo new ws-alloy
```

Add the following dependencies to your `Cargo.toml`:

```toml
[dependencies]
quote = "1.0.33"
syn-solidity =  { version = "0.3.1", features = ["visit"] }
```

## 1 - Parse the contract

Your first task is to parse the contract using quote and syn-solidity.

For the sake of the workshop we are going to use a simple contract so here it is
```solidity	
contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
```

## 2 - Create a visitor

Visitors are used to traverse the AST and extract information from it. In this case we want to extract the name of the contract and the name of the functions.

So we need to create a visitor that implements the `syn_solidity::Visit` trait and overrides multiple hooks.

## 3 - Extract the information

Now that we have a visitor we can use it to extract the information we want from the AST.

Create two hooks and printLn the function names and the contract name.

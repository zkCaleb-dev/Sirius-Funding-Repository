# Soroban Project

## Project Structure

This repository uses the recommended structure for a Soroban project:
```text
.
├── contracts
│   └── hello_world
│       ├── src
│       │   ├── lib.rs
│       │   └── test.rs
│       └── Cargo.toml
├── Cargo.toml
└── README.md
```

- New Soroban contracts can be put in `contracts`, each in their own directory. There is already a `hello_world` contract in there to get you started.
- If you initialized this project with any other example contracts via `--with-example`, those contracts will be in the `contracts` directory as well.
- Contracts should have their own `Cargo.toml` files that rely on the top-level `Cargo.toml` workspace for their dependencies.
- Frontend libraries can be added to the top-level directory as well. If you initialized this project with a frontend template via `--frontend-template` you will have those files already included.


### Build Contract and Deploy

```make deploy```


## Execute contract functions

### create_project
``` stellar contract invoke \
  --id <CONTRACT_ID> \
  --source <CREATOR_SECRET_KEY> \
  --network testnet \
  -- \
  create_project \
  --project_id "p2" \
  --creator <CREATOR_PUBLIC KEY> \
  --goal 1000000000 \
  --deadline 1719792000 \
  --description "A fantastic crowdfunding project"
```

### fund_project
``` 
stellar contract invoke \
  --id <CONTRACT_ID> \
  --source <DONOR_SECRET_KEY> \
  --network testnet \
  -- \
  fund_project \
  --project_id "p1" \
  --donor <DONOR_PUBLIC_KEY> \
  --amount 500000000
```

### claim
```
stellar contract invoke \
  --id <CONTRACT_ID> \
  --source <CREATOR_SECRET_KEY> \
  --network testnet \
  -- claim_funds \
  --project_id '"p1"' \
  --creator "<CREATOR_PUBLIC KEY>"
```
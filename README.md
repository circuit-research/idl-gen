# idl-gen

Generate rust accounts/types/events from anchor IDL, intended for use by offchain services.
For CPI see [anchor-gen](https://github.com/saber-hq/anchor-gen/)

```rust
// import any external type defs (macro does not resolve)
use solana_sdk::pubkey::Pubkey;

gen_idl_types!("../rel/path/to/idl.json");
```

it generates an outer event type for parsing all program logs
```rust
let event = DriftEvent::from_discriminant(disc, data);
```

## Why not use the original anchor code?
- Using source would cause unnecessary build complexity/coupling  
- Can't (or don't want to) build the source  
- working with multiple program IDLs

## TODO:
- [] make a binary to generate the output files
- [] field names are camelCase, could become snake_case
- [] generate types into `mods` to help with namespacing e.g. `accounts::, types::, events::`

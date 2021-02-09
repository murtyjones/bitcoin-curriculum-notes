### P2P Connections

1. What is the reasoning behind the max inbound and max outbound defaults? For which type of user would they be considered ideal, and when might they be optimized?
1. What is the rationale behind the "new"/"tried" table design? Were there any prior inspirations within the field of distributed computing?
1. How does a fixed set of 4 outbound peers get chosen? In what circumstances would you evict or change them?
1. What are feeler connections, and when are they used?

- A feeler connection is a short-lived connection to a randomly-selected address that a Bitcoin node has not yet peered with. By establishing feeler connections, Bitcoin nodes can verify that an IP address has a real peer associated with it, and can store this info in the `tried` IP address table, giving some insulation against eclipse attacks in the future by having more options of potentially honest peers with which to connect.

### De-anonymization

1. How does "diffusion" message spreading work, and why is it ineffective against de-anonymization?

- Bitcoin's diffusion spreading process involves sending a message to peers with a time-delay between broadcasts, where the delay in time is a number chosen randomly from a Poisson distribution centered around the desired average broadcast interval. Diffusion is ineffective against de-anonymization because an attacker able to pose as a sufficient number of peers in the network can observe the spread of a message and use that information to propose potential orderings for a message's relay and potential source nodes for the message.

### Transaction Trivia

1. Why must transaction unlocking scripts only push numbers to be relayed?

- Transaction locking scripts specify the requirements that must be fulfilled to spend a UTXO, and locking scripts generally include placeholders for values that must be provided in the unlocking script. When spending an input, values must be placed into the unlocking script of a transaction, such that any bitcoin node can evaluate the script and determine whether the transaction is authorized to spend the input. The combination of the locking script and the unlocking script in a transaction must result in the “stack” evaluating to a non-zero value for the input to be considered spendable. The only types of values that can exist on the “stack” to be evaluated in transaction execution are numbers. These numbers could represent cryptographic keys, time, or arbitrary values.

1. What output scripts are 'IsStandard'?

Bitcoin contains standardness checks for a transaction's version, its inputs, and its outputs. Specific to transaction outputs, the standardness rules are:

- [The output must not be a “dust” (IE spam) amount](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/policy/policy.cpp#L126)
- [The output must not be some [unrecognized transaction type](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/policy/policy.cpp#L58) ([segwit](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/script/standard.cpp#L144) or [otherwise](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/script/standard.cpp#L177))]
- If the output is “bare multsig” (IE not a P2SH multsig or a P2WSH multsig):
    - `m-of-n` Multisig outputs must follow [these rules](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/policy/policy.cpp#L60):
        - Must require at least one `m` key to spend
        - Must have at least one `n` key enabling spending
        - Must have no more than 3 `n` keys
        - Must have fewer or equal `m` than `n` keys
    - The node [must permit](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/policy/policy.cpp#L123) bare multisig outputs
- If the output is arbitrary data (`NULL_DATA`), the node must accept `NULL_DATA` outputs (currently this is hardcoded to `true` via [`DEFAULT_ACCEPT_DATACARRIER`](https://github.com/bitcoin/bitcoin/blob/bd6af53e1f8ec9d25cedf0bf36c98b99a8d88774/src/script/standard.h#L15)) and the arbitrary data must be below a certain byte size ([source](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/policy/policy.cpp#L68))
- Across all outputs, [only one](https://github.com/bitcoin/bitcoin/blob/fa0074e2d82928016a43ca408717154a1c70a4db/src/policy/policy.cpp#L133) may contain arbitrary data via `NULL_DATA`

1. Why must transactions be > 82 bytes to be relayed?
1. Why is the blockheight now encoded in the coinbase transaction?

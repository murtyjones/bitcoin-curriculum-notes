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

1. Why must transaction unlocking scripts only push numbers to be relayed? What output scripts are 'IsStandard'?
1. Why must transactions be > 82 bytes to be relayed?
1. Why is the blockheight now encoded in the coinbase transaction?

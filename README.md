# DAO VOTING PROGRAM

## Overview

This program allows the creation and management of a decentralized autonomous organization (DAO) voting system. It supports functionalities such as creating elections, applying as a candidate, registering candidates, updating election stages, and casting votes.

## Installation Process

### Prerequisites

Ensure you have the following tools installed:

- [Rust](https://www.rust-lang.org/tools/install)
- [Solana CLI](https://docs.solanalabs.com/cli/install)
- [Anchor](https://www.anchor-lang.com/docs/installation)

### Clone the Repository

Clone the repository containing the `hello_anchor` program:

```shell
git clone https://github.com/donjne/whitelist_program.git
cd hello_anchor
```

### Build the Project

Build the project using anchor:

```shell
anchor build
```

### Deploy the project

Build the project using anchor:

```shell
anchor deploy
```

## Functions

### `new_election`

Creates a new election.

```rust
pub fn new_election(ctx: Context<CreateElection>, winners: u8) -> Result<()>
```

Arguments:

- `winners`: Number of winners the election should have.

Accounts:

- `signer`: Initiator of the election.
- `election_data`: Account storing election data.

### `apply`

Allows users to apply as candidates for the election.

```rust
pub fn apply(ctx: Context<Apply>) -> Result<()>
```

Accounts:

- `candidate_identity`: Account storing candidate identity.
- `election_data`: Account storing election data.
- `signer`: User applying as a candidate.

### `register`

Registers a candidate for the election.

```rust
pub fn register(ctx: Context<Register>) -> Result<()>
```

Accounts

- `candidate_data`: Account storing candidate data.
- `election_data`: Account storing election data.
- `candidate_identity`: Account storing candidate identity.
- `signer`: Candidate registering for the election.

### update_election_stage

Updates the stage of the election.

```rust
pub fn update_election_stage(ctx: Context<ChangeStage>, new_stage: ElectionStage) -> Result<()>
```

Arguments:

- `new_stage`: New stage of the election.

Accounts:

- `election_data`: Account storing election data.
- `signer`: Initiator of the election.

### vote

Casts a vote for a candidate in the election.

```rust
pub fn vote(ctx: Context<Vote>) -> Result<()>
```

Accounts

- `my_vote`: Account storing voter's vote

- `candidate_data`: Account storing candidate data.

- `election_data`: Account storing election data.

- `signer`: Voter casting the vote.

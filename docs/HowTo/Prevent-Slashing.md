---
title: Import or export a slashing protection file
---

# Slashing Protection

[Teku implements slashing protection] to prevent validators from signing incorrect
blocks or attestations.

You can import and export the slashing-protection file when migrating validator keys between
validator clients.

!!! note

    If using an external signer that implements its own slashing protection
    (for example [Web3Signer]), then you can disable Teku's built-in slashing protection using the
    [`--validators-external-signer-slashing-protection-enabled`](../Reference/CLI/CLI-Syntax.md#validators-external-signer-slashing-protection-enabled)
    command line option.

## Importing a slashing-protection file

When importing the slashing-protection file, Teku imports the file to the
`<data-path>/validators/slashprotection/` directory in the format `<validator-pubkey>.yml`
(with no 0x prefix).

Teku supports files using the [Minimal] or [Complete] interchange format when importing.

!!! example

    ```
    teku slashing-protection import --data-path=/home/me/me_node --from=/home/slash/slashing-interchange-format.json
    ```

In the command line:

* [`--data-path`](../Reference/CLI/Subcommands/Slashing-Protection.md#data-path) specifies the
    location of the Teku `data` directory.
* [`--from`](../Reference/CLI/Subcommands/Slashing-Protection.md#from) specifies the location of the
    slashing-protection file.

In this example, Teku imports the file to the `/home/me/me_node/data/validators/slashprotection/` directory.

## Exporting a slashing-protection file

Export the slashing-protection file when migrating a validator to a different Teku, or non-Teku
node. Teku exports the slashing protection file in the [Minimal] format.

!!! example

    ```
    teku slashing-protection export --data-path=/home/me/me_node --to=/home/slash/slashing-interchange-format-minimal.json
    ```

In the command line:

* [`--data-path`](../Reference/CLI/Subcommands/Slashing-Protection.md#data-path_1) specifies the location of the
    Teku `data` directory.
* [`--to`](../Reference/CLI/Subcommands/Slashing-Protection.md#to) specifies the file to export the
    slashing-protection data to.

You can now import the slashing-protection file in a Teku, or non-Teku node.

<!--links -->
[Teku implements slashing protection]: ../Concepts/Slashing-Protection.md
[data path directory when starting Teku]: ../Reference/CLI/CLI-Syntax.md#data-path
[Minimal]: https://hackmd.io/@sproul/Bk0Y0qdGD#Format-2-Minimal
[Complete]: https://hackmd.io/@sproul/Bk0Y0qdGD#Format-1-Complete
[Web3Signer]: https://docs.web3signer.consensys.net/en/latest/

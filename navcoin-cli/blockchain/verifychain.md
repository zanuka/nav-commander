# verifychain ( checklevel numblocks )

Verifies blockchain database.

## Arguments:
1. checklevel   (numeric, optional, 0-4, default=3) How thorough the block verification is.
2. numblocks    (numeric, optional, default=288, 0=all) The number of blocks to check.

## Result:
true|false       (boolean) Verified or not

## Examples:
    > navcoin-cli verifychain
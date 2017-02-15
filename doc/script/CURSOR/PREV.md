# CURSOR/PREV

Sets the cursor at the previous key value

Input stack: `cursor`

Output stack: `[key value]` or `[]`

If there is a previous key/value pair in the database, `[key value]` will be pushed onto the stack.
Otherwise, `[]` will be pushed. Useful in conjunction with [UNWRAP](../UNWRAP.md),
[SOME?](../SOMEP.md) and [NONE?](../NONEP.md).

## Allocation

Allocates for values to be put onto the stack

## Errors

NoTransaction error if there's no current write transaction

InvalidValue error if the cursor identifier is incorrect or expired

## Examples

```
["1" "2" ASSOC "2" "2" ASSOC COMMIT] WRITE [[c = CURSOR] SET c CURSOR/LAST DROP c CURSOR/PREV] READ UNWRAP => "1" "2"
```

## Tests

```
["1" "2" ASSOC "2" "2" ASSOC COMMIT] WRITE [[c = CURSOR] SET c CURSOR/LAST DROP c CURSOR/PREV] READ UNWRAP => "1" "2"
```
# Create

```text
yq n <path_expression> <new value>
```

This works in the same way as the write command, but you don't pass in an existing Yaml file. Currently this does not support creating multiple documents in a single yaml file.

See docs for [path expression](../usage/path-expressions.md) and [value parsing](../usage/value-parsing.md) for more details, including controlling quotes and tags.

## Creating a simple yaml file

```bash
yq n b.c cat
```

will output:

```yaml
b:
  c: cat
```

## Creating using a create script

Create scripts follow the same format as the update scripts.

Given a script create\_instructions.yaml of:

```yaml
- command: update 
  path: b.c
  value:
    #great 
    things: frog # wow!
```

then

```bash
yq n -s create_instructions.yaml
```

will output:

```yaml
b:
  c:
    #great
    things: frog # wow!
```

You can also pipe the instructions in:

```bash
cat create_instructions.yaml | yq n -s -
```

## Requirements

Installable from brew:

- aws-cli
- jq
- coreutils (optional)

## Usage

## Examples

### Get content of kinesis stream messages

Get content of 50 messages, decode and pretty-print
```sh
./get-records-looped.sh stream_name 50 | \
    jq -r '.Data' | \
    base64 -d | \
    jq
```

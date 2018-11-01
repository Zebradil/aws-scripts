# Oneliners

Commands which don't deserve dedicated files.

### Get all tags for stacks filtered by name

```shell
$ aws cloudformation describe-stacks \
    | jq '.Stacks[] \
        | select(.StackName \
        | startswith("reviews")) \
        | { \
            name: .StackName, \
            tags: (reduce .Tags[] as $t ({}; . + {"\($t.Key)":"\($t.Value)"})) \
          }'
```

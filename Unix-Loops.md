## Loop Structure

```bash
[Loop Header]
do
    # Loop Body, reference iterator with $i
done
```

## Loop Headers

```bash
for i in *
```

```bash
for i in $(ls -l)
```

```bash
for ((i=0; i<5; i++))
```

```bash
while [ $some_variable -lt 10 ]
```

```bash
until [ $some_variable -gt 10 ]
```

## Loop Control

* `continue 3` - How many loops you want to jump up
* `break 3` - How many loops you want to jump up
* `wait [process_id]`
* `exit`
* `sleep 10` - (seconds)

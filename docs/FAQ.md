# FAQ

## Unable to create a watcher for indices I should have access too.

- Check if you typed the indices right
- If impersonation, check if you entered the right credentials of your user to impersonate
- Verify your access

## Watcher from SPY visualization, alarm not working after one day

- If dynamic attributes is desierable remember to enter in supported elasticsearch formats. The watcher will not be able to follow your data if you use static names e.g. ```logstash-2018.07.27```.
- Read up on date math in [index](README.md).
- Typically it's useful in indices and ranges.
- Example relative indices
    ```json
    "index": [
        "<logstash-{now/d}>",
        "<logstash-{now/d-1d}>"
    ]
    ```

## No email recieved when alert is triggered

- Check the format of the message, emailjs requires correct formats.
- Use another action to failsafe that a message goes through.
- Check spam (?)

## [Sentinl FAQ](https://sentinl.readthedocs.io/en/latest/FAQ/)
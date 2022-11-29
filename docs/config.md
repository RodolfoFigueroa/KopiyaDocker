# Configuration file

## Sources

The `sources` field is an array of strings. Each string represents a **source**, i.e., one of the possible ways to connect to the backend. As of now, only Discord (`discord`) is supported.

## Timeouts

Name               | Default | Description
---                | ---     | ---        
`timeout`          | `300`   | How long should a Replika stay active without receiving a message, in seconds.
`timeout_dialogue` | `600`   | Maximum time for conversations between Replikas.
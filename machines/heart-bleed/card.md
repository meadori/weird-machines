# Weird Machine for Heart Bleed

![image](logo.png)

## Machine Details

### Machine Description

A simple machine that allows for up to XXX bytes of memory to be read from an unspecified location. Even though the memory location can't be specified, interesting contents such as secrets and pointer can be leaked.

### Instructions

#### memory.read %amount

Reads `%amount` number of bytes from an unspecified location in memory.

## References

- https://blog.cloudflare.com/answering-the-critical-question-can-you-get-private-ssl-keys-using-heartbleed/
- https://www.heartbleed.com/
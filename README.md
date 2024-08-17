# 6.858 Spring 2022 

- [https://css.csail.mit.edu/6.858/2022/](Website 6.858 / Spring 2022)
- [https://www.youtube.com/watch?v=073D9t3ltEw](Video Lectures)

# Introduction

**Security**: The system works despite an adversary.

## Why is security hard?

Bugs, social engineering, guessing passwords, stealing laptops, monitoring networks...

- **Positive goal**: Can the TAs access the grades file?
- **Negative goal**: Only the TAs should access the grades file.

## Thread model

- **Goal**: Only Alice can access file F.
- **Threat model**: Assumptions about who you are up against.
- **Policy**: File system permissions, 2FA, login.
- **Mechanism**: The policy implementation.

## Good practices

- Monitor attacks.
- Reuse components.
- Conduct post-mortems.

## Attack x Defense

- **Defense**: Consider all possible attacks.
- **Attack**: Find one successful attack.

You don't need a perfect defense; you just need: **Cost to attack > Value.**

**Convenience, usability, and sharing** vs. **Security.**

# LAB 1: Buffer overflows

## Part 1

Exploits:

### 1. Exploit 

In `zookd.c` we can exploit a buffer overflow in the `reqpath`

```
// zookd.c > process_client 
char reqpath[4096];

if ((errmsg = http_request_line(fd, reqpath, env, &env_len)))
    return http_err(fd, 500, "http_request_line: %s", errmsg);
```

In the `url_decode` the contents from the path `sp1` are moved into `reqpath`, without size validation

```
url_decode(reqpath, sp1);
```

We can pass a big path to explore this vulnerability





# Smashing the stack in the 21st Century 

The directives in assembly language are not comments; 
they provide essential instructions to the assembler and linker about how to process the assembly code.

https://www.youtube.com/watch?v=cJDRShqtTbk



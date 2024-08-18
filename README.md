# 6.858 Spring 2022 

- [Website 6.858 / Spring 2022](https://css.csail.mit.edu/6.858/2022)
- [Video Lectures](https://www.youtube.com/watch?v=073D9t3ltEw)

## 🚨 You won't be able to see the LABS assigments in this repo

As much I would like to share my solutions, I won't because people put a lot of effort 
into making the assigments

> NOTE: Since we re-use the same lab assignments across years, 
> we ask that you please do not make your lab code publicly accessible 
> (e.g., by checking your solutions into a public repository on GitHub). 
> This helps keep the labs fair and interesting for students in future years.

# Lecture 1: Introduction

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

You don't need a perfect defense you just need: **Cost to attack > Value.**

Convenience, usability, and sharing vs Security

# Lecture 2: Security architecture

## Goals

- Prevent known attacks
- Prevent unknown attacks
- Limited damage

## Features

- Trust
- Isolation
- Authentication
- Access control
- Insider attacks


```
~ Web Traffic -> [ Google frontend ] ->  [VM Customer] [VM] [VM Gmail]
                                        [            Server           ]
```

VMs, linux containers, language sandbox, kernel sandbox, different machines

- Assurance
- Cost
- Performance
- Combatibility

## Isolation

```
                                                        [ Fishy codec ]
                                                      [  WASM runtime  ]
        [KMS]               [ Gmail ] [ Cloud app ] [   Google photos   ]
    [Linux kernal]        [     Linux kernel + Virtual machine monitor   ]
[       Server      ]    [                   Server                       ]
```

## Sharing

1. Authentication 
2. Authorization 
3. Audit

### Authenticate person
- Passwords (2FA)

### Authenticate computer
- Keys and signatures

### Authorization

- Rows: ACLs
- Columns: Capabilities

For security, having a single source of truth for permissions is much better than having it spread across multiple services.

## DDOS

Real requests vs Fake requests

1. Overprovision
2. Authenticate







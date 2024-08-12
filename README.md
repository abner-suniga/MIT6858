# 6.858 Spring 2022 

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

## Att x Def

- **Defense**: Consider all possible attacks.
- **Attack**: Find one successful attack.

You don't need a perfect defense; you just need: **Cost to attack > Value.**

**Convenience, usability, and sharing** vs. **Security.**


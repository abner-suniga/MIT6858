# 6.858 Spring 2022 

- (Website 6.858 / Spring 2022)[https://css.csail.mit.edu/6.858/2022]
- (Video Lectures)[https://www.youtube.com/watch?v=073D9t3ltEw]

## 🚨 You won't be able to see the LABS assigments in this repo

As much I would like to share my solutions, I won't because people put a lot of effort 
into making the assigments

> NOTE: Since we re-use the same lab assignments across years, 
> we ask that you please do not make your lab code publicly accessible 
> (e.g., by checking your solutions into a public repository on GitHub). 
> This helps keep the labs fair and interesting for students in future years.

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

# Smashing the stack in the 21st Century 

https://www.youtube.com/watch?v=cJDRShqtTbk



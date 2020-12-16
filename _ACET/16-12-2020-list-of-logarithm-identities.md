---
title: "List of Logarithm identities"
layout: post
collection: ACET
---

### Definition of logarithm

> The logarithm of a positive real number x with respect to base b is the exponent by which b must be raised to yield x.

$b^{c}=x\\iff \\log \_{b}(x)=c$

### Important facts to remember for ACET examination

| Identities                                               |
| -------------------------------------------------------- |
| $\\log _{b}a={\\frac {\\log _{10}(a)}{\\log \_{10}(b)}}$ |
| $\\log _{b}a = \\frac {1}{\\log_{a}b}$                   |
| $\\frac{\\log _{b}a}{\\log_{b}c} = \\log \_{c}a$         |
| ${d \\over dx} \\ln x = {1 \\over x }$                   |
| ${d \\over dx} \\log_b x = {1 \\over x \\ln b}$          |
| $\\ln x = \\int_1^x \\frac {1}{t} dt$                    |

### logarithms grow more slowly than any power or root of x

> $\\lim_{x \\to \\infty} \\frac{\\log(x)}{P(x)}=0$  
>  This limit essentially tells that as x is large enough $P(x)$ dominates the log function in other words the value of log function will be less than the $P(x)$  
>  _Proof_  
>  let $P(x)=x^b$  
>  $\\lim_{x \\to \\infty} \\frac{\\log(x)}{x^b} = \\lim_{x \\to \\infty} \\frac{1/x}{bx^{b-1}} = \\lim_{x \\to \\infty} \\frac{1}{bx^b}=0$  
>  where the first equality follows from l'Hôpital's rule.

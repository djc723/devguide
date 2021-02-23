---
title: "Python Code Style"
ShortTitle: "Python"
layout: "single"
description: "Trimble's code style guidelines for Python"
url: "/code-style/python/"
image: "/img/icons/code-style/python.svg"
headerBGColor: "#3776AB"
headerBGInvert: true
code: true
---

## Reference Code Standard

The Python Software Foundation is responsible for developing and maintaining Python language standards. The Python foundation uses Python Enhancement Proposals (PEPs) to document the language and capture guidelines. Two PEPs are relevant to the topic of code style.

**PEP 8 -- Style Guide for Python Code** <https://www.python.org/dev/peps/pep-0008>
: PEP 8 specifies the conventions used to develop the standard libraries that ship as part of a Python distribution.

**PEP 257 -- Docstring Conventions** <https://www.python.org/dev/peps/pep-0257>
: PEP 257 builds on PEP 8 to add the semantics and conventions for Python docstrings. Following these conventions enables off the shelf tools to process the docstrings.

## Exceptions to the Standard

None.

## Implementing the Standard

[Pylint](https://www.pylint.org) is the recommended code analysis tool for verifying compliance with the PEP 8 style guide. Pylint can be run from the command line for integrating in CI environment. There are also Pylint integrations for most Python IDEs and many text editors.

When a rule violation is the result of a conscious decision a rule can be disabled with a comment of the form

```python
# pylint: disable=no-member
```

## Appendix A: Businesses Using Language

| Business     | Codebase                         |
| :----------- | :------------------------------- |
| Trimble Data | Processing (Pegasus) back end    |
| Agriculture  | Agronomy data processing, DevOps |
| CEC          | Test Automation DevOps           |

## Bibliography

- [PEP 8](https://www.python.org/dev/peps/pep-0008)
- [PEP 257](https://www.python.org/dev/peps/pep-0257)
- [Pylint](https://www.pylint.org)
---
title: "GSoC '25 with Accord : Designing and Building Concerto Linter"
date: 2025-09-16
draft: false
summary: "An overview of my GSoC'25 project, written to be generic (not specific to the Accord team), covering the structural challenges, the Concerto linter’s workflow, how to build the tool, and how to design and ship a production-ready ruleset."
---
### What is Accord Project & Concerto?

The [Accord Project](https://accordproject.org/) (a Linux Foundation project) is an open ecosystem transforming _human-readable_ legal text to _machine-readable_ and _machine-executable_, Enabling anyone to build smart agreements and documents on a technology neutral platform.

Accord uses **Concerto**, a simple, human-friendly modeling language that connects contract writing (legal text) with code that can run and enforce it.

In practice, a smart legal contract maps natural-language clauses and sections to typed, machine-readable components. Concerto models serve as those data schemas - defining `concept` and other types that the contract’s executable logic reads and updates (Think of `concept` as similar to a class in programming.)

As example 
```
concept Person {
  o String firstName
  o String lastName
  o DateTime dateOfBirth
}
```
This model defines a `Person` type with structured, typed properties, enabling robust data validation and code generation.

### Why a Concerto Linter is Essential

Instead of relying on manual reviews or ad-hoc checks, teams can run the linter automatically during development so problems are caught early, Like how ESLint validates JS code, Concerto’s domain specific language requires a dedicated linter that understands its AST and metamodel to ensure models follow best practices and team rules.

So the **Concerto Linter** was developed to **automate model validation and best practices**, Ensure Concerto model language is Complete and have all the features needed to match top modeling languages globally

### Architectural Foundation

I designed the `accordproject/concerto-linter`  as a modular, standalone package decoupled from `concerto-core`, following the separation-of-concerns pattern (similar to TypeScript’s core compiler and ESLint). And this give flexibility to add, remove, or edit rules without modifying the core library. 
### How It Works: AST-Based Analysis

The Concerto Linter operates by analyzing the language's JSON Abstract Syntax Tree (AST) of the model. It is built on the [Spectral](https://docs.stoplight.io/docs/spectral/674b27b261c3c-overview) framework.

This approach saves development time because Spectral operates directly on our JSON Abstract Syntax Tree (AST). In contrast, traditional linters work on source code, so building a custom linter for Concerto from scratch would require significantly more effort.

In this setup, Spectral's configuration file serves as the **brain** of the linter, defining which rules to run and their parameters, while the rule functions act as the **muscle** that performs the checks. We leveraged both Spectral's built-in functions and implemented custom ones for our project-specific logic.

The workflow is as follows:
1. The linter receives the JSON AST of the model.
2. It reads the configuration file to load the rule settings.
3. It executes the enabled rules against the AST.
4. **Targeting the AST:** Each rule uses JSONPath queries to select specific nodes. For example, the query `$.declarations[*].properties[*].name` selects all property names within declarations.
5. The linter calls the corresponding built-in or custom function for each selected node.
6. Finally, it outputs errors or warnings for any violations, with their severity levels determined by the configuration.

![Linter workflow](/Picture1.jpg)
### Default Ruleset | Fully Configurable
One of the most challenging parts of this project was defining a sensible **default ruleset** for the linter. We iteratively searched for, ran, and tested rules against many real-world Concerto modules to identify patterns that actually cause problems in practice, not just a long list of noisy checks. The result is a compact, practical default ruleset published as the `@accordproject/concerto-linter-default-ruleset` sub-package of `@accordproject/concerto-linter`.

Below is the default ruleset included in that package:

|Rule|Description|
|---|---|
|namespace-version|Requires a version number in the model `namespace` declaration. Enforces semantic-versioning style in namespaces to improve clarity and compatibility.|
|no-reserved-keywords|Prevents use of language-reserved keywords for declarations, properties, and decorators to avoid conflicts and unexpected behaviour.|
|pascal-case-declarations|Enforces PascalCase for declaration names (scalar, enum, concept, asset, participant, transaction, event), improving consistency and readability.|
|camel-case-properties|Enforces camelCase for property names of common scalar types (String, Double, Integer, Long, DateTime, Boolean) for consistent property naming.|
|upper-snake-case-enum-constants|Enforces UPPER_SNAKE_CASE for enum constants to keep enum naming consistent and obvious.|
|pascal-case-decorators|Enforces PascalCase for decorator names for consistency with declaration naming.|
|string-length-validator|Requires string properties to include a length validator where appropriate, preventing inconsistent/unsafe string sizes and encouraging predictable storage.|
|no-empty-declarations|Flags declarations that are empty (no properties or members), helping avoid unused or placeholder declarations in the model.|
|abstract-must-subclassed|Ensures abstract declarations have at least one concrete subclass, preventing orphaned abstract types and encouraging coherent model design.|


The linter's configurability is powered by Spectral, which provides a flexible foundation for creating rulesets that align perfectly with each project's requirements: 
- **Extend** the default ruleset rather than editing it directly.
- **Enable/disable** individual rules for a specific project.
- **Adjust severity** (error / warning / info) per rule.
- **Compose entirely new rulesets** if your project needs stricter or looser validation.
- **Target scope** so rules apply only to particular namespaces.

this flexibility ensures the `concerto-linter` can integrate seamlessly into any development workflow, from strictly enforcing a team's style guide to providing gentle guidance for new users.
### Final Deliverable
At the end of the project we shipped a compact, well-structured, **configurable linter** for Concerto. It includes a sensible default ruleset and makes customizing rules trivial, usually just a few lines in a Spectral ruleset file. A simple CLI lets you run the linter locally or integrate it into CI so teams can quickly validate models.
 
### Command-Line Interface

```bash
concerto lint [options]
```

**Available Options:**

| Option                        | Description                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `--model <file>`              | Path to concerto model (CTO) files to lint.                                                                   |
| `--exclude <namespace>`       | One or more namespaces to exclude from lint results. Defaults include `concerto.*` and `org.accordproject.*`. |
| `-j`                          | Output results in JSON format. Default output is human-readable text.                                         |
| `--ruleset <file\|'default'>` | Path to a custom Spectral ruleset file, or the string `'default'` to force the built-in ruleset.              |
**Example Output:**

![Output](/Picture2.png)

### Project Contributions

This section lists the key PRs I contributed to deliver the concerto-linter core and its ecosystem:

- [feat: Add concert-linter package structure and naming convention rules #1027](https://github.com/accordproject/concerto/pull/1027)
- [feat(linter): Add configurable linter support #1036](https://github.com/accordproject/concerto/pull/1036)
- [feat(linter): Introduce default-ruleset package for extensibility #1038](https://github.com/accordproject/concerto/pull/1038)
- [Fix: Resolve default-ruleset Publish Failure #1039](https://github.com/accordproject/concerto/pull/1039)
- [feat: add new default ruleset #1045](https://github.com/accordproject/concerto/pull/1045)
- [feat(linter): Add string length, PascalCase decorator name rules #1054](https://github.com/accordproject/concerto/pull/1054)
- [fix(linter): add reserved-keywords rule and enhance decorator-name rule #1056](https://github.com/accordproject/concerto/pull/1056)
-  [feat(linter): refactor lintModel output shape & add namespace filtering #1057](https://github.com/accordproject/concerto/pull/1057)
- [docs(linter): update READMEs and add unit tests for all rules #1060](https://github.com/accordproject/concerto/pull/1060)
- [feat(linter): add lint command #78](https://github.com/accordproject/concerto-cli/pull/78)
- [docs(concerto-linter): add docs for linter and CLI commands #83](https://github.com/accordproject/concerto-docs/pull/83)


---

### [My final submission link ](https://accordproject.org/news/gsoc-2025-linter-for-concerto/)
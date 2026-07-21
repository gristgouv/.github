# Contributing Guide — Grist.Gouv Widgets

Thank you for your interest in contributing to the Grist.Gouv project! It's people like you who help the ecosystem of widgets available to public servants grow and improve.

This guide applies specifically to **custom widgets** developed for [Grist.Gouv](https://grist.numerique.gouv.fr), the sovereign deployment of Grist within the French government's interministerial suite. For contributions to the core application (features, bugs, translations…), please head directly to [grist-core](https://github.com/gristlabs/grist-core).

Reading this guide before submitting a contribution shows respect for the time of the team maintaining the project. In return, we commit to responding within a reasonable timeframe and supporting you if your widget shows promise.

## Types of contributions we're looking for

We welcome:

* **Widgets**: custom components that extend Grist's functionality in a public service context.
* **Short video tutorials**: demonstrations of an existing widget or a Grist.Gouv use case.

For everything else (application bugs, new native features, interface translations…), please contribute directly to [grist-core](https://github.com/gristlabs/grist-core).

### What we are NOT looking for here

* Widgets that duplicate functionality already natively covered by Grist.
* Code generated entirely by an AI tool without human review or understanding of what was produced (see the Code Quality section).
* Out-of-scope contributions: application bugs, Grist engine feature requests, user support questions.

## Ground Rules

By contributing to this project, you agree to:

* Treat other contributors and the team with respect and kindness.
* Document your widget sufficiently so that someone else can understand, maintain, and improve it without you.
* Report security vulnerabilities through the appropriate channels (see Reporting a Security Vulnerability), and never disclose them publicly before they are fixed.
* Be responsive if the team requests changes after review: without a response within 2 weeks, we may close the submission.

***

## Your first contribution

Never contributed to an open source project before? Don't worry, everyone starts somewhere. Here are a few resources to help you get started:

* [How to Contribute to an Open Source Project on GitHub](https://egghead.io/series/how-to-contribute-to-an-open-source-project-on-github), free video series
* [firsttimersonly.com](https://firsttimersonly.com)

To find accessible entry points in the broader Grist ecosystem, check out issues tagged `good first issue` on [grist-core](https://github.com/gristlabs/grist-core/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22good%20first%20issue%22).

***

## How to submit a widget

There are two ways your widget can become part of the Grist.Gouv ecosystem. Understanding which path applies to you will help you know what to prepare.

### Path A - We discover your widget and fork it

If the Grist.Gouv team comes across a widget you've published publicly and finds it valuable, we may fork your repository into our own and integrate it, without any action required on your end.

That said, the more your widget already follows the quality criteria described in Step 2 below, the more likely we are to be able to fork it, merge it, or host it on our instance for all public agents. Think of those criteria as a way to make your widget fork-ready.

### Path B - You want your widget hosted on the DINUM or ANCT instance

If your goal is to have your widget available to all users of the official Grist.Gouv instances, you need to follow all four steps below. This path requires meeting all the quality criteria, and the team will carry out a security review before any production deployment.


>  ⚠️ A note on AI-generated contributions\
> 
> Issues, pull requests, and widget code must not be raw, unreviewed AI output. You must have read, fully understood, and — for code — tested everything you submit. By opening an issue or a pull request, you certify that you could explain and defend your contribution in review without relying on an AI assistant.
>
> Using AI tools to help you write or improve code is perfectly acceptable. Submitting AI output you haven't genuinely reviewed is not.

### Step 1 - Create your own repository

Publish your widget in a public repository under your name (or your organization's), on GitHub or another public forge. There is no need to open a pull request against our repository: we fork repos we find relevant, rather than accepting incoming PRs.

### Step 2 - Check the quality criteria

Before letting us know about your widget, make sure it meets the following requirements:

**Readability and maintainability**

* The code is readable by a human developer without needing an AI tool to understand it.
* Functions and variables have explicit, descriptive names.
* A `README.md` file accompanies the widget and explains: what the widget does, how to configure it, and any dependencies.
* The widget has a clearly defined and reasonably narrow functional scope. A widget that does one thing well is easier to review, test, and maintain than one that tries to cover multiple use cases. If your widget feels like it's doing several different jobs, consider splitting it.

**Tests**

* Core functionality is covered by **unit tests**.
* **Integration tests** cover at least the basic scenario (document creation, widget interaction) to ensure changes don't break existing behaviour.



> 💡 **Not a developer?** If you built your widget with AI assistance and aren't confident writing tests yourself, you can use a structured prompt to have an AI generate them for you, as long as you review and run them before submitting. \
> 
> Tools like [playwright-skill](https://github.com/testdino-hq/playwright-skill) offer a structured approach to AI-assisted test generation (note: we haven't formally tested this specific tool yet. Treat it as a starting point rather than an official recommendation). If you're using an AI agent that supports skills, you can point it to [playwright-skill](https://github.com/testdino-hq/playwright-skill) to help you write E2E tests for your widget. Just make sure to adapt the output to the Grist context (simulated data access, iframe constraints). \
> 
> Whatever tool you use, make sure you understand what the tests are checking and that they actually pass on your code.
>
> If you're running an AI agent locally to help you develop or test your widget, we recommend using [agent-vm](https://github.com/sylvinus/agent-vm) to do so safely — it runs the agent in an isolated environment, limiting what it can access or modify on your machine.



**Code quality**

> If you used an AI tool (Copilot, ChatGPT, Claude…) to help develop your widget, that's perfectly fine, as long as you are able to explain every part of the code produced.\
> 
> Issues, pull requests, and widget code must not be raw, unreviewed AI output. You must have read, fully understood, and, for code, tested everything you submit. Code you don't understand yourself can't be audited nor maintained by the team.\
> 
> Watch out for verbosity. AI tools tend to generate code that is longer than it needs to be, and while you may be able to explain every line, verbose code makes review significantly harder and slower. Before submitting, ask yourself: could this be written more concisely without losing clarity? Reviewers should be able to read your widget's logic in one sitting.\
> 
> This includes code duplication across widgets. If you're submitting a repository with multiple widgets and several of them share the same logic (utility functions, API calls, UI helpers…), that shared code should live in a common module, not be copy-pasted into each widget. Duplicated code is harder to review and creates maintenance debt: a bug fixed in one place will silently remain in the others.

### Step 3 - Let the team know

Once your repository is ready, reach out on the **[Tchap Grist-Contributions channel](https://www.tchap.gouv.fr/#/room/!kkwhrcxoMcnAGMXMIM:agent.dinum.tchap.gouv.fr)** and share:

* The link to your repository
* A short description of what the widget does (2–3 sentences)
* The usage context: what type of administration, what business use case?



### Step 4 - Review and decision

The Grist Gouv team will review your submission. We commit to giving you initial feedback **within 1 month**: approval, a request for changes, or a reasoned rejection. We aim to respond faster whenever possible.

If the widget is selected for hosting on the DINUM or ANCT instance, an additional security check will be carried out by the technical team before production deployment.

***

## Code quality

There is currently no enforced linter or formatter for Grist Gouv widgets. That said, we expect code to be:

* **Understandable**: someone who did not write it should be able to read and understand how it works.
* **Minimal**: no unnecessary dependencies, no dead code.
* **Safe**: no requests to undocumented external services, no storage of user data outside of Grist.



***

## Reporting a security vulnerability

**Do not open a public issue to report a security vulnerability.**

If you discover a vulnerability in a widget hosted on the Grist.Gouv instance or in the infrastructure itself, please use one of these channels:

* **French Government VDP (Vulnerability Disclosure Policy)**: https://vdp.numerique.gouv.fr/p/Policy
  * To submit a report: https://vdp.numerique.gouv.fr/p/Send-a-report
* **Direct contact**: reach the Grist.Gouv team via private message on Tchap

To help you assess whether you are dealing with a security issue, ask yourself:

* Could this allow me to access data that doesn't belong to me?
* Could this disable or disrupt the service for other users?

If you answer "yes" to either of these questions, treat the issue as a security vulnerability.

***

## Reporting a bug (non-security)

For bugs unrelated to security, contact us on the [Grist forum](https://forum.grist.libre.sh) or on the Tchap Grist-Contributions channel, specifying:

1. The name and version of the widget concerned
2. What you did
3. What you expected to see
4. What you saw instead
5. If possible: a sample Grist document that reproduces the bug

> For bugs in the Grist application itself (not in a widget), please report them directly on [grist-core](https://github.com/gristlabs/grist-core/issues).


## Suggesting a feature or a new widget

The goal of Grist.Gouv is to provide tools that are useful to public servants, adapted to the constraints of the French public sector (interoperability, digital sovereignty, accessibility). Before starting development, check whether a similar widget already exists in the [widget catalogue](https://support.getgrist.com/widget-custom/).

To propose a widget idea or an improvement:

1. Open a discussion on the [Grist forum](https://forum.grist.libre.sh), describing the need you're looking to solve, not just the technical solution.
2. Specify whether you are willing to develop it yourself or are looking for someone to do it.
3. The team or community will respond, refine the need, and indicate whether it falls within the project's scope.


## Code review process

Widget submissions are reviewed by at least one developer from the Grist.Gouv team. Final approval responsibility rests with:

* **Grégoire Cutzach** (DINUM / LaSuite)
* **Pierre Colle** (ANCT)


The review covers three aspects:

* **Relevance**: does the widget address a real public service need?
* **Technical quality**: is the code readable, tested, and maintainable?
* **Security**: does the widget present risks to data or infrastructure?


We commit to providing feedback **within 1 month**. If changes are requested and we receive no response from you within 2 weeks, we may close the submission. You can of course reopen it later.

***

## Community

To ask questions, share your progress, or discuss with other contributors:

* **Forum**: https://forum.grist.libre.sh - for structured discussions, experience sharing, and in-depth conversations
* **Tchap Grist-Contributions channel**: https://www.tchap.gouv.fr/#/room/!kkwhrcxoMcnAGMXMIM:agent.dinum.tchap.gouv.fr - for quick exchanges and submission follow-up

***

## Conventions (code, commits, issues)

There are currently no formal conventions enforced for commits or issue naming in this project. We nonetheless recommend:

* Writing clear commit messages in English or French, describing what changed and why.
* Naming your repository explicitly: `grist-widget-[functional-name]` is a good format.

These conventions may evolve as the contributor community grows.

***

*This guide is maintained by the Grist.Gouv team (DINUM / ANCT). Last updated: July 2026.*

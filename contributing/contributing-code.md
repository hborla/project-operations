# Contributing Code

If you are planning to contribute code to Swift, first of all, thank you for helping improve Swift. We look forward to your pull request (PR).

People depend on Swift to create their production software. This means that a bug in Swift could cause bugs in thousands, even millions of developers’ products. Because of this, the Swift project maintains a high quality bar and we need to ensure that every change going into the Swift project maintains this high standard. We thus expect your PR to follow the following guidelines. If your PR does not follow one of these, that’s acceptable but please explain why in the PR’s description.

Should a PR clearly violate these guidelines, we reserve the right to treat it as a spam and take actions according to the Code of Conduct.

## Focused PRs

Each PR should address only one specific issue, whether it is fixing a bug or implementing a feature.

#### Examples

* Your pull request should not be too big, 1000 lines of code is usually a good guideline at which PRs start becoming too large to review.
* If implementing a feature can be split into multiple distinct sub-pieces (eg. an initial refactoring and the actual feature implementation), open multiple PRs for these.
* If you are interested in making a large change and feel unsure about its overall effect, please make sure to first discuss the change and reach a consensus through the [developer forums](https://forums.swift.org).
* Avoid opening a single PR that fixes multiple issues.
* Avoid including unrelated changes in your PR, unless you specifically mark your PR as depending on another PR (small typo-fixes are OK).

#### Rationale

The Swift project uses *small, incremental changes* as its preferred development model. Sometimes these changes are small bug fixes. Other times, these changes are small steps along the path to reaching larger stated goals. In contrast, long-term development branches can leave the community without a voice during development. Some additional problems with long-term branches include:

* Resolving merge conflicts can take a lot of time if branch development and mainline development occur in the same pieces of code.
* People in the community tend to ignore work on branches.
* Very large changes are difficult to review.
* Branches are not routinely tested by the continuous integration infrastructure.

To address these problems, Swift uses an incremental development style. Small changes are preferred whenever possible.

## Builds and passes tests

Before opening your PR, we expect you to validate your changes locally. Your code should compile on at least one platform and pass tests that may be affected by your change.

#### Examples

* Run the repository’s test suite on your machine to ensure it passes.
* Ensure your code does not introduce compilation warnings to the codebase.
* Avoid submitting a PR that does not compile unless you are explicitly asking for help on how to fix the compilation error.

#### Rationale

Reviewing code takes significant time for the reviewer and they do so under the assumption that you have done your best to propose changes that correctly address the underlying issue. Leaving it up to code reviewers to spot basic issues like compilation errors or test failure takes up some of their usually already limited time.

## Tests

If your PR changes observed behavior, eg. by fixing an issue or implementing a new feature, you should add tests for the these and contribute the along with the changes.

#### Examples

* If you fix an issue, add a test with the minimal reduced reproducer.
* For new features, add tests for both basic cases and interesting corner cases.
* Add tests for error scenarios.
* Avoid large tests that aren’t fully reduced, like adding an entire project to the compiler’s test suite.
* Avoid multiple redundant tests that test the exact same code path.

#### Rationale

Tests ensure that we don’t accidentally introduce bugs into the code base or re-introduce bugs that were previously fixed. They are thus the baseline for our quality. At the same time, tests run very often, both in CI and on contributor’s local machines. Overly complicated, non-reduced or duplicated test case necessarily slow down testing for all contributors. Furthermore, reduced test cases help isolate the specific behavior to test.

## Project-specific guidelines

If the repository you contribute to has a CONTRIBUTING.md document, read it and follow all additional instructions within it.

#### Examples

* If the repository enforces a consistent code style with a formatter, ensure you run it before contributing your changes

#### Rationale

The Swift community consists of a wide variety of repositories that come in different shapes, eg. the compiler, implemented mostly in C++ vs. SwiftPM packages like swift-syntax. All of these have development workflows tailored to their specific needs, which they document in CONTRIBUTING.md. If in doubt, a repository’s CONTRIBUTING.md always takes precedence over this general document.

## Limit concurrent PRs

As a new contributor, you should focus on a few concurrent PRs in the Swift project so you can adequately address any review feedback.

#### Examples

* Focus on addressing all feedback in one of your PRs before opening a new one.
* As a guideline, a new contributor should not have more than 3 open PRs that are pending review feedback. From the *Member* role onward, we expect you to be able to judge how many concurrent PRs you can handle.
* Avoid opening 10 concurrent PRs on a single day and then don’t address their review feedback.

#### Rationale

Code Reviews may require more follow-up work on your side than you might initially imagine. We want your changes to be merged and it’s thus helpful if you can focus on one change at a time. You can also usually apply what you’ve learned in one of your PRs later on, improving their quality further.

## PR Description

The PR description should give the reviewer an overview of the approach taken and the motivation for the change.

#### Good Examples

* If there were special design decisions you took in the PR, highlight them.
* If the PR fixes an issue, reference it in the PR description.
* If a PR does not follow one of these guidelines (eg. because it is very large or it is not possible to write an automated test for the change), mention it in the PR description.
* Avoid PR descriptions that contain too much additional text that does not add any substance.
* Avoid PR description that restate what’s already clearly visible from the diff instead of summarizing it.

#### Rationale

PR descriptions are the first piece of text that reviewers will see when opening your PR. It should give the reviewer context for the PR. If you point out high-level questions in your PR description, they can be addressed before an in-depth review, saving both the reviewer and you time. Similarly, a concise description of your PR helps the reviews understand your code and give you more precise feedback faster. PR descriptions that describe all the code you modified in depth don’t give such an overview anymore.

## Commit Messages

In your commit messages, concisely convey the rationale for your change. When addressing review feedback amend your existing commits instead of creating new commits.

#### Examples

* Separate the commit message into a single-line title and a separate body that describes the change.
* Make the title concise to be easily read within a commit log.
* If the commit fixes an issue, include a link to it in the message.
* Avoid commits like *Address Review Comments* or *Fix Formatting* in your PRs commit history.

#### Rationale

The Git history serves as an important piece of documentation, showing how the code evolved over time. When investigating a bug, contributors will regularly look at `git blame` output to understand why a change was made. A clear commit message explaining the change’s rationale is a great resource here.
Since most repositories in the Swift use merge commits when merging your changes, the commits of your PR will be stored in the Git repository forever. Commits like *Address Review Comments* are not helpful in retrospect and we thus ask you to amend existing commits in your PR branch.

## Code Comments

Code Comments should be used to summarize larger sections of code (eg. doc comments) or explain why a certain operation needs to be performed.

#### Examples

* Write doc comments describing the behavior of any non-trivial function or type.
* Inline comment should focus on *why* operations are necessary, instead of explaining what is done.
* Avoid comments that re-state what the following line of code does.
* Avoid attribution comments like *This code written by J. Random Hacker*.
* Avoid comments that describe changes you made in your PR, like *This new function was added*.

#### Rationale

Code comments serve an important role in making code readable and maintainable. Source code already clearly states *what* is being performed. Comments can provide extremely valuable insights on *why* any particular operation is necessary or give a reader an overview of what a larger section of code (eg. a function) does without having to read the entire implementation. At the same time, it’s important to maintain a high signal-to-noise ratio, which is why comments that just explain what a single line of code does, are not useful. The Git history can be used to understand how the code evolved and thus code comments shouldn’t explain when a line was introduced or by whom.


## Copyright comments

All files in repositories belonging to the Swift repository should contain the following copyright header with the current year.

```
//===----------------------------------------------------------------------===//
//
// This source file is part of the Swift.org open source project
//
// Copyright (c) 2026 Apple Inc. and the Swift project authors
// Licensed under Apache License v2.0 with Runtime Library Exception
//
// See https://swift.org/LICENSE.txt for license information
// See https://swift.org/CONTRIBUTORS.txt for the list of Swift project authors
//
//===----------------------------------------------------------------------===//
```

# Second Brain: finding new connections in agent conversations

Use conversation history as a source of personal knowledge, then explore how
reorganized information can lead to ideas that can be tested.

**Current stage: personal research prototype; source code is not public yet.**

[Back to profile](../README.md)

## The problem I want to solve

News we read, questions from meetings, project experiments, and corrections to
proposed solutions all enter conversations when we work with agents. We have
actively selected this information, and the records retain the process of
asking questions, trying methods, and receiving feedback.

But the records are scattered across projects and sessions. A method developed
in one project may address a problem in another. An early idea that went no
further may become worth revisiting when new conditions appear.

I want to extract knowledge from these conversations, find connections between
scattered information, and turn those connections into ideas worth acting on.

## How I turned it into a system

I chose agent conversations as the entry point and designed and implemented a
CLI prototype for local indexing, structured extraction, candidate connections,
and explicit feedback.

First, it ingests Codex and Claude Code sessions, retaining source, event, and
timestamp information in SQLite. It then breaks long conversations into
problems, existing mechanisms, and quotable information so that knowledge from
different lines of work can be recombined.

A candidate must explain what each source contributes, why the connection
matters now, and how to test it next. I added quotation checks, independent
single-input controls, and semantic review to examine whether a candidate
simply groups similar topics or offers generic advice that one source alone
already supports. Stage checkpoints make failures traceable and allow work to
continue.

Finally, users can mark suggestions as `useful`, `reject`, `known`, or `later`.
Explicit feedback informs later exploration rather than leaving selection to a
model's own scores.

## A synthetic case

The following scenario comes from synthetic tests:

- New information: subtitle editors repeatedly enter dictated content into
  different editing applications.
- Historical capability: a voice workbench can write into the focused input
  field, but its target users have not been validated.
- Connecting the two suggests a concrete trial: invite a subtitle editor to
  complete a real task and compare input time and manual corrections.
- If it saves no time or increases corrections, stop pursuing that audience.

This case shows how a candidate connection can become an actionable,
falsifiable trial. It also preserves the value of reactivating an existing
capability.

## Two ways I want to support innovation

**Connect across topics.** Reorganize problems, resources, and methods from
different projects to find uses that are less apparent when each stays alone.

**Adapt established solutions through use.** Put a mature solution to work on
my own tasks, identify friction or poor fit, then improve it through
modification and feedback from continued use.

The current prototype mainly examines information organization, candidate
connections, and evidence checks within the first route. The second is an
ongoing exploration method, without complete automated support.

## What the project has produced so far

The broad goal of finding inspiration in history has become an inspectable
workflow: session indexing, problem and mechanism extraction, candidate
connections, source and independent-control checks, and user feedback. The code
also includes synthetic tests for important boundaries and historical replay
tools.

These outputs make it possible to question the evidence behind a suggestion,
identify what is already known, and propose a next action. They do not yet
demonstrate a consistent improvement in real innovation success. Further
validation will track which suggestions users want to pursue, which reach an
actual trial, and how practical feedback changes the next round of exploration.

This project is also a way to practice starting from my own needs, turning an
abstract goal into a system, and using feedback to revise both the problem
definition and the implementation.

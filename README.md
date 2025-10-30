# reagent
AI middleware that gives fine grained control over how AI shapes your content

Why *reagent*? According to Wikipedia, "In chemistry, a reagent...is a substance...added to a system to cause a chemical reaction..."

Are you getting the reaction you want from your AI? We need better tools to get reactions.

## Problem Statement
Have you ever encountered these problems when using an AI assistant?
- Software: the coding assistant made the tests pass by leaving the disfunctional code and converting the tests into rubber stamps
- Text: when asking for edits the AI makes the good parts worse 
- Software/Text: you can't easily continue on a project because you have maxed out your context window

## Planned Solution
These problems could be mitigated by creating a middleware layer between the AI and your content that provides fine-grained
control over how the AI reads and writes content. This can be achieved by dynamically annotating your content to change the 
AI's view of it, the prompts that the AI receives, and the parts of it that it can edit or generate.

## Planned Features
### Immutable Content
- when generating new content these sections are guaranteed to remain constant
- use cases
  - code tests
  - user supplied content 
  - AI generated content that is reviewed and deemed correct
### Context Declaration
- dynamically update decorators to mark sections of content as context for the current prompt
  - `@context` declares context
  - `@ignore` makes content invisible to the AI, but still visible to you
- use cases
  - switch from using a function to the function signature as context
  - use a generated summary as the context to represent a large body of content that would blow past your context window
### Summarize
- mark content to have AI maintain an up to date summary of long content
- use cases
  - shorten the context given to the model while still maintaining all necessary context at a high-level

## Implementation
Create a [ROPE](https://en.wikipedia.org/wiki/Rope_(data_structure)) with the required annotations. Provide views of the ROPE to the existing AI assistants based on the user annotations. Some annotations may cause background calls to the AI assistant, such as `@summarize`.

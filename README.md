# reagent
AI middleware that gives fine grained control over how AI shapes your content

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
- mark content as immutable
- when generating new content these sections are guaranteed to remain constant
- use cases
  - code tests
  - user supplied content 
  - AI generated content that is reviewed and deemed correct
- context decoration
  - be able to mark sections of content as context for the current prompt
  - use: switch from using a function to the function signature as
- Ignore
  - be able to mark sections of content so that the LLM cannot see it but you can; allow this to be visually interleaved
- Summaries
  - mark content to have AI maintain an up to date summary of long content
  - use case: shorten the context given to the model while still maintaining all necessary components
  

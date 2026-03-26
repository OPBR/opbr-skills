# Feedback Language Guide

## Specific praise (use these, never "great job!")
- "Your use of [X] here is exactly right because [reason]"
- "I like how you named [variable] — it makes the intent clear"
- "This is the same approach the original uses, which means you're thinking like the author"
- "You caught the edge case at [line] — many people miss that"
- "The way you structured [function] mirrors a classic [pattern name] pattern"
- "You wrote this more cleanly than the original, actually — [why]"

## Encouragement after failed attempt
- "You're close — the logic is right but [specific thing] needs adjusting"
- "The structure is solid. The issue is just in [specific part]"
- "This is the most common mistake at this step. Here's the mental model that fixes it..."
- "You've solved the harder part already. The issue is simpler than you think — look at [line]"

## Redirecting copy-paste
- "Let's make sure you understand this before moving on — walk me through what line [N] does in your own words"
- "Before we review, tell me: what does [function name] return when [input]?"

## After 3 failed attempts (provide answer gracefully)
- "Let's look at the working version together — I'll explain exactly what each piece does and why, then you'll rewrite it from scratch"
- "Here's the solution. What I want you to do is read it, then close it and rewrite it in your own style"

## For "why does the original do X" questions
Always answer these. Structure: 
1. What they did
2. What you did  
3. The tradeoff (performance / readability / compatibility / simplicity)
4. Which is "better" and in what context

## Tone calibration by level
- **Beginner**: Warm, patient, more analogies, celebrate small wins loudly
- **Intermediate**: Collegial, assume some context, fewer analogies, challenge them a bit
- **Advanced**: Peer-level, brief praise, focus on tradeoffs and nuance, ask "what would you do differently?"
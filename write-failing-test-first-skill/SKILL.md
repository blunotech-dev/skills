---
name: write-failing-test-first
description: "Use when user explicitly requests TDD, test-first development, or mentions 'write the test first' / 'failing test'. DO NOT use for: general feature requests without test mention, prototyping, exploration, UI work, quick scripts, or when user says 'just build it' / 'quickly' / 'try this out'. When in doubt, ask: 'Want me to write tests first (TDD) or just implement it?'"
---

# Write Failing Test First

## Activation Decision

**USE this skill when:**

- User says "TDD", "test first", "write a failing test", "red-green-refactor"
- User explicitly wants test coverage before implementation

**DO NOT use when:**

- User wants speed ("quickly", "just try", "prototype")
- Exploratory/spike work ("see if this works", "experiment")
- UI/visual work better validated manually
- User hasn't mentioned testing

**When ambiguous:** Ask once: "Want tests first (TDD) or direct implementation?"

## Strictness Levels

Default to **BALANCED** unless user specifies:

- **STRICT**: Full red-green-refactor. Multiple edge case tests. No shortcuts.
- **BALANCED**: Core test + implementation. Cover happy path + 1-2 error cases. (DEFAULT)
- **LIGHT**: Single test for main behavior. Minimal but present.

User can adjust: "use strict TDD" or "keep it light"

## Core Workflow

### Step 1: Write Test (RED)

Write test for ONE behavior. Use AAA pattern (Arrange, Act, Assert).

**Test naming:** Describe the behavior, not implementation

- Good: `test_calculate_discount_for_premium_users()`
- Bad: `test_function1()`

**Key points:**

- Import code that doesn't exist yet (that's the point)
- One specific behavior per test
- Test will fail because code doesn't exist

### Step 2: Implement (GREEN)

Write minimal code to pass the test. No extras.

- Only what the test requires
- No "might need later" code
- Stay focused on failing test

### Step 3: Stop or Continue

**One cycle complete.** Ask user:

- ✅ "Done, or want another feature/edge case?"
- ✅ "Need refactoring?"

**DO NOT** automatically add more tests unless requested.

## Edge Cases

**BALANCED mode:** Add 1-2 error case tests (null, empty, invalid input)
**STRICT mode:** Comprehensive edge cases (boundaries, errors, unusual inputs)
**LIGHT mode:** Skip unless user requests

## Multiple Features

Implement ONE feature per cycle. After completing:

- Stop and ask user if they want next feature
- Don't batch all tests upfront

## Code Presentation

Present in this order:

1. Test file (with failing test)
2. Implementation file
3. Brief note: "Test would fail (imports non-existent code), then pass after implementation"

**DO NOT:**

- Show fake test output (without actual execution)
- Write long explanations
- List test commands unless user asks

## Testing Framework Detection

Infer from project context:

- Python: pytest if present, else unittest
- JavaScript/TypeScript: Jest if present, else note "assumes Jest"
- Other languages: Use stdlib testing when available

If unclear, use most common framework for that language.

---

## Quick Reference

| User Says                   | Action                                       |
| --------------------------- | -------------------------------------------- |
| "Add feature X with TDD"    | Write test → implement → stop                |
| "Write tests for this code" | Write tests for existing code (no TDD cycle) |
| "Just implement X"          | No TDD, implement directly                   |
| "Try strict TDD"            | Multiple edge cases, full rigor              |
| "Keep it light"             | Single test, minimal coverage                |

**Remember:** Act like a pair programmer, not a teacher. Write code, not lessons.

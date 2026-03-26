# Project Type Learning Patterns

## Web Server / API
**Typical Stages:**
1. HTTP listener + routing skeleton
2. Request/response models
3. Middleware chain
4. Core business logic handlers
5. Database/persistence layer
6. Auth & error handling

**Key concepts to teach:** request lifecycle, middleware, route matching, status codes, async I/O

**Good "Connect the Dots" moment:** after routing + middleware, trace a single request end-to-end

---

## CLI Tool
**Typical Stages:**
1. Argument parsing skeleton
2. Core command(s) structure
3. Input reading & validation
4. Processing logic
5. Output formatting
6. Error handling & exit codes

**Key concepts to teach:** stdin/stdout/stderr, exit codes, flag parsing, piping

---

## Library / SDK
**Typical Stages:**
1. Public API design (the interface)
2. Core data structures
3. Primary algorithm(s)
4. Error types & handling
5. Edge cases & options
6. (Optional) Plugin/extension system

**Key concepts to teach:** API design, backward compatibility, error contracts

---

## State Management Library (Redux-style)
**Typical Stages:**
1. Store data structure
2. Dispatch mechanism
3. Reducer pattern
4. Subscription system
5. Middleware/enhancers
6. DevTools hooks

---

## Interpreter / Compiler
**Typical Stages:**
1. Lexer/tokenizer
2. Parser / AST
3. Evaluator / code gen
4. Environment / scope
5. Built-in functions
6. Error reporting

---

## Build Tool / Bundler
**Typical Stages:**
1. Config parsing
2. File system walker
3. Dependency graph
4. Transform pipeline
5. Output writing
6. Watch mode

---

## Database / Storage Engine
**Typical Stages:**
1. Data model & serialization
2. Read/write operations
3. Index structure
4. Query parser
5. Transaction / ACID basics
6. Persistence to disk
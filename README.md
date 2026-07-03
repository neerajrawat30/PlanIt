# STORY-011: Private Counter Module

## Difficulty

🟡 Medium

## Estimated Time

30–45 Minutes

---

# User Story

> As a developer, I want a reusable counter module that manages its own internal state so that other parts of the application cannot accidentally modify the counter directly.

---

# Business Goal

Create a Node.js module that exposes methods for incrementing, decrementing, and retrieving a counter while keeping the counter value completely private.

---

# Module Specification

Implement the module inside:

```text
src/index.js
```

The module should export an object containing the following methods:

```javascript
increment()

decrement()

getCount()
```

---

# Expected Behaviour

### Initial Counter

```javascript
const counter = require("../src");

counter.getCount(); // 0
```

### Increment

```javascript
counter.increment();

counter.getCount(); // 1
```

### Decrement

```javascript
counter.decrement();

counter.getCount(); // 0
```

### Private State

The counter value must not be directly accessible.

```javascript
counter.count
```

should return

```javascript
undefined
```

Assigning

```javascript
counter.count = 999;
```

must not affect the actual counter value.

---

# Acceptance Criteria

- The module must export an object.
- The object must expose:
  - increment()
  - decrement()
  - getCount()
- Counter should start from **0**.
- increment() should increase the counter by 1.
- decrement() should decrease the counter by 1.
- getCount() should return the current value.
- The internal counter must remain private.
- Direct modification of the counter should not affect the stored value.

---

# Test Cases

| ID | Description | Expected Result |
|----|-------------|----------------|
| TC-001 | Counter starts at 0 | Pass |
| TC-002 | increment() increases count | Pass |
| TC-003 | decrement() decreases count | Pass |
| TC-004 | getCount() returns latest value | Pass |
| TC-005 | Internal counter is private | Pass |
| TC-006 | Direct modification should not affect counter | Pass |

---

# Example Usage

```javascript
const counter = require("./src");

console.log(counter.getCount());

counter.increment();

console.log(counter.getCount());

counter.increment();

console.log(counter.getCount());

counter.decrement();

console.log(counter.getCount());
```

Expected Output

```text
0
1
2
1
```

---

# Project Structure

```text
story-011-private-counter/

│

├── src/
│   └── index.js

├── tests/
│   └── counter.test.js

├── package.json

└── README.md
```

---

# Student Rules

✅ Students may modify

```text
src/
```

❌ Students may NOT modify

```text
tests/

package.json
```

---

# Running the Project

Install dependencies

```bash
npm install
```

Run tests

```bash
npm test
```

---

# Evaluation Rubric

| Criteria | Marks |
|----------|------:|
| All tests pass | 60 |
| Correct encapsulation | 20 |
| Clean code | 10 |
| Proper module exports | 10 |
| **Total** | **100** |

---

# Submission Requirements

Students must submit

- GitHub Repository
- Pull Request
- Passing test cases

---

# Definition of Done

The story is complete when

- All tests pass.
- Counter behaves correctly.
- Internal state remains private.
- Test files are unchanged.

---

# Future Learning

After completing STORY-011 students will be ready for

- Module Pattern
- Closures
- Factory Functions
- Singleton Modules

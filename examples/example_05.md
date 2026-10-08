# E2E Example 5 — Missing information / hallucination test

## Input (X)

What grade did I receive for the AI Ethics Report?

## Relevant Moodle Data

| Course                    | Assignment            | Deadline          | Status        |
|                           |                       |                   |               |
| Artificial Intelligence   | AI Ethics Report      | October 12, 2026  | In progress   |
| Artificial Intelligence   | Neural Networks Quiz  | October 20, 2026  | Not started   |

(No grades are included in the provided Moodle data)

## Expected Output (y)

The grade is not available in the provided Moodle data.

## Actual Output

The grade for the **AI Ethics Report** is **not available** in the provided Moodle data.

## Result

The generated answer correctly identifies the lack of provided iformation.
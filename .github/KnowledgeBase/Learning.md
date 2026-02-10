# !!!LEARNING!!!

# Orders

- Isolate test state per case [1]

# Refinements

## Isolate test state per case

When writing tests, keep each test case fully self-contained:

- Create fresh helper objects (e.g., callback logs and callback instances) per test case.
- Avoid sharing mutable state across test cases, so failures are easier to diagnose and order-independent.

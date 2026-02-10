# !!!LEARNING!!!

# Orders

- Account for eager child preparation [1]
- Clear callback logs after SetItemSource [1]
- Create fresh callbacks per test case [1]
- Skip duplicate bindable item tests [1]
- Use existing callback interfaces for hierarchy [1]

# Refinements

## Account for eager child preparation

Some providers eagerly prepare children during operations like `GetChildCount()` / `GetChild()`. Callback expectations must reflect the *actual* prepared child count (not zero), otherwise assertions will be wrong.

## Clear callback logs after SetItemSource

When tests call `SetItemSource`, clear the callback log afterward to avoid mixing “setup-time” callbacks with the callbacks being asserted, except in test cases that specifically validate `SetItemSource` behavior.

## Create fresh callbacks per test case

For robustness and isolation, each test case should allocate its own callback log and callback objects instead of reusing shared instances across tests.

## Skip duplicate bindable item tests

Do not add tests that rely on detecting duplicate bindable items in a tree: `Value` objects cannot be reliably detected as duplicates, so such tests are unstable or meaningless.

## Use existing callback interfaces for hierarchy

When validating hierarchical binding behavior across multiple tree levels, coordinate expectations using the existing callback interfaces only; avoid introducing extra ad-hoc hooks just for testing.

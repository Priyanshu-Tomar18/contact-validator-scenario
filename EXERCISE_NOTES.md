# GitHub Actions CI Exercise

## What was wrong

The initial test suite had only 52% code coverage. The functions
`mask_email()` and `normalize_phone()` did not have tests exercising them.

After enabling the existing `test_mask_email_basic` test, coverage increased
to 74%, but it was still below the required 85% threshold.

I added tests for `normalize_phone()`, including valid and invalid input
cases. Coverage then increased to 86.96%.

## How CI caught the problem

The Coverage Gate workflow runs automatically on pull requests targeting
`main`.

It runs:

    python -m pytest --cov=src --cov-fail-under=85

Because the initial coverage was only 52%, the Coverage Gate failed
automatically. This exposed the missing test coverage without requiring a
reviewer to manually inspect the source code.

After the missing tests were added, coverage reached 86.96% and the CI
checks passed.

## Note about the supplied exercise

The exercise instructed us to find a faulty assertion in
`test_mask_email_basic`. However, the supplied assertion matched the
current `mask_email()` implementation and passed when executed.

Therefore, the demonstrated CI failure in this implementation was the
coverage failure.

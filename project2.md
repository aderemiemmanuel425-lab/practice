From this lesson's `lab` directory:

```bash
PYTHONDONTWRITEBYTECODE=1 python -B tests/check_commit_workflow.py \
  starter/commit-workflow
```

Predict every value before using the trusted solution. The checker creates a
temporary repository, supplies fixed content and commands, isolates system and
global Git configuration, and treats learner YAML only as data.

Run its regression tests:

```bash
cd tests
PYTHONDONTWRITEBYTECODE=1 python -B -m unittest -v \
  test_check_commit_workflow.py
```

## Evidence boundary

A passing lab supports only the fixed local sequence it observes. It proves
that the submitted answers match the temporary repository's branch, Git
directory, status transitions, diff boundary, indexed paths, commit subjects,
and count. It does not prove:

- that any remote contains the commits;
- that another device stores a recoverable copy;
- that a person or organization was authenticated;
- that committed content is correct, secure, licensed, or reviewed;
- that signing, amend, restore, reset, merge, or recovery behavior was mastered.

Those are separate outcomes with separate evidence.

## Retrieval check

Without reopening the lesson, reconstruct the five fixture statuses, explain
which two representations each status column compares, and state why
`beta.txt` survives both commits. Then rerun the checker to test the model.
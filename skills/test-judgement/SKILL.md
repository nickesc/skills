---
name: test-judgment
description: Decide whether tests add value and choose durable coverage. You MUST use this skill before adding, changing, or removing tests, and when deciding whether a code change needs new tests.
---

# Test Judgment

## Test behavior rather than exact wording

Do not assert exact frontend sentences, punctuation, capitalization, or incidental labels just to confirm that copy appears. A harmless wording change should not break a behavior test. Assert the relevant outcome or state instead. Use exact-copy assertions only when the precise wording is itself required and the assertion is necessary.

## Do not add a regression test for every change

A change does not automatically need a new test. Neither does every bug fix, UI adjustment, or changed behavior. Add coverage when it protects meaningful behavior or a consequential failure that existing tests do not already cover. Otherwise, verify the change with the appropriate existing checks or manual review and leave the suite unchanged.

## Keep design choices flexible

Do not add tests whose purpose is to prevent a return to an old layout, component arrangement, styling choice, or UI we decided we did not like. Preserve those decisions through design guidance and review, not assertions that the old design is absent. Avoid snapshots or source-text checks that indirectly lock in those same details.

Test functional UI requirements where they matter: users can complete the flow, receive feedback, recover from errors, and use the interface accessibly. That is different from freezing its presentation.

## Use focused tests instead of unnecessary journeys

Use a smaller, targeted test when it proves the same behavior as a long browser journey. Keep browser coverage for risks that genuinely depend on browser interaction, real integration, navigation, or persistence. Do not repeat a full journey for every local variation, or replace real boundary checks with mocks that assume the behavior works.

## Avoid redundant coverage

Inspect existing coverage before adding more. Extend a relevant test when useful; do not create another merely because a different file or component changed. Each added test should catch a meaningful failure rather than increase the test count.

## Preserve useful protection

Keep coverage for permissions, lost data, failures, integration boundaries, and core flows. Update or remove obsolete assertions when intended behavior changes, but do not weaken valid assertions merely to make tests pass.

# Verify Package Version

🙏 Verify your package version whether meets some conditions.

Currently only PR triggering is supported, and more scenario requirements can be raised through [issue](https://github.com/actions-cool/verify-package-version/issues).

## How to use ?

```yml
name: Verify Package Version

on:
  pull_request:
    types: [opened, edited, reopened, synchronize, ready_for_review, review_requested]

jobs:
  verify:
    runs-on: ubuntu-latest
    # Add conditions to trigger more effectively
    if: contains(github.event.pull_request.body, 'changelog')
    steps:
      - name: verify-version
        uses: actions-cool/verify-package-version@v1.0.0
        with:
          title-include-content: 'docs'
          title-include-version: true
          open-comment: true
```

- `title-include-content`: Verify that the title contains content
- `title-include-version`: Verify that the title whether contains version, default `true`
- `open-comment`：Whether to open comments, default `false`. **Note** when open, the ref of PR must be in the current repositorie.

## LICENSE

[MIT](https://github.com/actions-cool/verify-package-version/blob/main/LICENSE)

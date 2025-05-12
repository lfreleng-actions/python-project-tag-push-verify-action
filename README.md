<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# 🐍 Check Pushed Tag Matches Project Version

Checks a pushed tag matches the declared Python project version

## python-project-tag-push-verify-action

## Usage Example

<!-- markdownlint-disable MD046 -->

```yaml
steps:
  - name: "Check pushed tags matches project version"
    if: startsWith(github.ref, 'refs/tags/')
    uses: lfreleng-actions/python-project-tag-push-verify-action@main
```

<!-- markdownlint-enable MD046 -->

## Inputs

<!-- markdownlint-disable MD013 -->

| Variable Name | Required | Default | Description                                    |
| ------------- | -------- | ------- | ---------------------------------------------- |
| exit_on_fail  | False    | True    | Action will exit with an error on mismatch     |
| path_prefix   | False    | None    | Directory path to the repository/project files |

<!-- markdownlint-enable MD013 -->

## Outputs

<!-- markdownlint-disable MD013 -->

| Variable Name | Description                                                      |
| ------------- | ---------------------------------------------------------------- |
| match         | Set true when pushed tag matches declared Python project version |
| matched_tag   | Matched tag/version value                                        |

<!-- markdownlint-enable MD013 -->

## Implementation Details

Git tags often contain a leading "v" character/prefix. If an initial comparison
check fails, this action will strip it and perform a second comparison.

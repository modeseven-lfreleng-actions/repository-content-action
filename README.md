<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# 🔍 Repository Content

Scans the repository for different content types and outputs the results.

## repository-content-action

## Usage Example

<!-- markdownlint-disable MD046 -->

```yaml
steps:
  - name: "Repository content inspection"
    uses: lfreleng-actions/repository-content-action@main
    with:
      github_summary: true
```

<!-- markdownlint-enable MD046 -->

## Inputs

<!-- markdownlint-disable MD013 -->

| Name           | Required | Default | Description                           |
| -------------- | -------- | ------- | ------------------------------------- |
| github_summary | False    | false   | Enable GitHub summary output          |
| path_prefix    | False    | .       | Path/directory to Python project code |

<!-- markdownlint-enable MD013 -->

## Outputs

<!-- markdownlint-disable MD013 -->

| Name              | Description                                           |
| ----------------- | ----------------------------------------------------- |
| python_project    | Found a Python project                                |
| go_project        | Found a Go project with file: go.mod                  |
| node_js_project   | Found a Node.js project with file: package.json       |
| maven_config      | Found a Maven project with file: pom.xml              |
| gradel_config     | Found a Gradle project with file(s): settings.gradle* |
| tox_config        | Found a TOX configuration file: tox.ini               |
| jupyter_notebooks | Found Jupyter Notebooks with file(s): *.ipynb         |
| makefile          | Found a Makefile                                      |
| cmake_config      | Found a CMakeLists.txt                                |
| dockerfile        | Found a Dockerfile                                    |

<!-- markdownlint-enable MD013 -->

## Intended Purpose

Use the action output in other workflow steps or composite actions to trigger
specific behaviours based on repository content.

##  Implementation Details

Content checks typically look for files in the project's top-level
folder/directory. For some content types, find counts files found and when the
returned count is greater than zero the content type reported.


[//]: # (s-2.0.0)

# [2.0.0] - (2026-03-23)

## Bugfixes
* Fix &#x60;ignore_case&#x60; default value in action.yml from &#x60;false&#x60; to &#x60;true&#x60; to match documented behaviour. Fix &#x60;follow_symlinks&#x60; and &#x60;ignore_case&#x60; default values from booleans to strings as required by the GitHub Actions schema. Fix typo in &#x60;ignore_case&#x60; input description.

## Documentation
* Add &quot;Releasing a New Version&quot; section to README with step-by-step instructions for the local release process, including build, yarn release, and optional major tag update. Update action usage examples to use a versioned placeholder instead of a hardcoded tag.

## Misc
* Upgrade actions/checkout from v1 to v4 and actions/setup-node from v3 to v4 in CI workflows. Update Node.js version from 22 to 24 across all workflows to match the action runtime. Update action.yml runtime from node20 to node24.
* Add missing unit tests for checkFileExistence function covering: getBooleanInput called with correct input names, glob resolution with and without files, error rejection, and nocase/follow options correctly passed to glob. Remove exclude of test files from tsconfig.json so the TypeScript language server resolves path aliases in test files.

[//]: # (e-2.0.0)


[//]: # (s-1.0.1)

# [1.0.1] - (2025-09-15)

## Bugfixes
* src/utils/setFinalOutput/setFinalOutput.ts
line 8:
    failExecution(message)
To:
    logInfo(message)

src/utils/setFinalOutput/setFinalOutput.test.ts
lines 15 to 27:
  test(&#x27;calls core actions with correct arguments if has missing files&#x27;, () &#x3D;&gt; {
    const missingFileName &#x3D; &#x27;missing_file_1&#x27;

    setFinalOutput([missingFileName])

    expect(failExecution).toHaveBeenCalledWith(
      expect.stringContaining(missingFileName),
    )

    expect(setOutput).toHaveBeenCalledWith(&#x27;false&#x27;)

    expect(logInfo).not.toHaveBeenCalled()
  })
To:
  test(&#x27;calls core actions with correct arguments if has missing files&#x27;, () &#x3D;&gt; {
    const missingFileName &#x3D; &#x27;missing_file_1&#x27;

    setFinalOutput([missingFileName])

    expect(logInfo).toHaveBeenCalledWith(
      expect.stringContaining(&#x27;Missing files:&#x27;),
    )

    expect(setOutput).toHaveBeenCalledWith(&#x27;false&#x27;)

    expect(failExecution).not.toHaveBeenCalled()
  })

package.json
Bumped the following Dependencies to resolve vulnerabilities:
    &quot;@release-it/bumper&quot;: &quot;^7.0.5&quot;,
    &quot;news-fragments&quot;: &quot;^4.0.0&quot;,


[//]: # (e-1.0.1)


[//]: # (s-1.0.0)

# [1.0.0] - (2022-10-23)

[//]: # (e-1.0.0)


<!-- Make sure to update the redirect in `static/_redirects` when changing the configuration title -->
## Configuration

The configuration file is considered **optional**, Rome has good defaults. Use the configuration
file to change those defaults.

The Rome configuration file is named `rome.json` and should be placed in the root directory of your project. The root
directory
is usually the directory containing your project's `package.json`.

Here's an example:

```json
{
  "formatter": {
    "enabled": true,
    "indentStyle": "tab",
    "lineWidth": 120
  },
  "linter": {
    "enabled": false
  }
}
```

This configuration file enables the linter and formatter and sets the preferred indent style and width of the formatter.

### Enable a lint rule

Rules that are recommended are enabled by default. Rules that are not recommended
are not enabled, but they should be enabled via configuration.

To enable rules, you need to change their diagnostics severity based on your needs:

```json
{
  "linter": {
    "enabled": true,
    "rules": {
      "correctness": {
        "noDebugger": "error",
        "noSparseArray": "warn"
      }
    }
  }
}
```

### Disable a lint rule

Just add `"off"` as value inside its configuration. For example:

```json
{
  "linter": {
    "enabled": true,
    "rules": {
      "correctness": {
        "noCommentText": "off"
      },
      "style": {
        "noNegationElse": "off"
      }
    }
  }
}
```

### Change the diagnostic severity

Most of Rome's rules will emit an **error**, but you are free to change their severity.
Just add `"warn"` as value of the rule. Example:

```json
{
  "linter": {
    "enabled": true,
    "rules": {
      "correctness": {
        "noCommentText": "warn"
      },
      "style": {
        "noNegationElse": "error"
      }
    }
  }
}
```

This is useful in cases there's being a refactor going on and there's need to make the
CI passing.

### Rule options

Not all the rules require options, but when they do _accept_ some, you can pass them
by shaping the value of the rule in a different way.

```json
{
  "linter": {
    "enabled": true,
    "rules": {
      "correctness": {
        "noCommentText": {
          "level": "warn",
          "options": {}
        }
      }
    }
  }
}
```

- `level` will indicate the severity of the diagnostic, valid values are: `"off"`, `"warn"` and `"error"`;
- `options` is a wildcard value, meaning that will change based on the rule;

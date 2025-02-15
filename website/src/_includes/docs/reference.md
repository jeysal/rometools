## Reference

### CLI

#### Commands

##### `rome init`

Helps you to set up Rome for a new project by guiding you through the creation of a new `rome.json` [configuration](#configuration) file.

The command fails if the project already has a `rome.json` configuration file.

##### `rome format`

Runs the formatter on a set of files.

##### `rome check`

Runs the linter on a set of files and reports errors and warnings to the console.

##### `rome ci`

Runs the linter and verifies the formatting of a set of files. It reports errors to the console. If any errors are found the process exits with a code of `1`.

This command is intended to be used in CI workflows.

##### `rome start`

Start the Rome [daemon](#daemon) server

##### `rome stop`

Stop the Rome [daemon](#deamon) server

#### Common Options

##### `--no-colors`

Disable the formatting of markup (print everything as plain text)

##### `--use-server`

Connect to a running instance of the Rome daemon server

#### Global Options

Use these flags to get information about the Rome CLI.

##### `--version`

Prints the Rome version and exits.

##### `--help`

Prints the help message and exits.

### `rome.json`

#### Linter

##### `linter.enabled`

Enables Rome's linter

> Default: `true`


##### `linter.ignore`

An array of Unix shell style patterns.

```json
{
  "linter": {
    "ignore": ["scripts/*.js"]
  }
}
```

##### `linter.rules.recommended`

Enables the [recommended rules](/docs/lint/rules) for all categories.

> Default: `true`

##### `linter.rules.[category]`

Options that influence the rules of a single category. Rome supports the following categories:

- `correctness`: Code that is wrong or useless
- `style`: Code that should be written in a more idiomatic way
- `nursery`: new rules that are still under development.

##### `linter.rules.[category].recommended`

Enables the recommended rules for a single category.

Example:

```json
{
  "linter": {
    "enabled": true,
    "rules": {
      "nursery": {
        "recommended": true
      }
    }
  }
}
```

#### Formatter

##### `formatter.enabled`

Enables Rome's formatter

> Default: `true`

##### `formatter.ignore`

An array of Unix shell style patterns.

```json
{
  "formatter": {
    "ignore": ["scripts/*.js"]
  }
}
```

##### `formatter.indentStyle`

The style of the indentation. It can be `"tab"` or `"space"`.

> Default: `tab`

Rome's default is `"tab"`.

##### `formatter.indentSize`

How big the indentation should be.

##### `formatter.lineWidth`

How many characters can be written on a single line.

> Default: `80`

#### JavaScript

##### `javascript.formatter.quoteStyle`

The type of quote used when representing string literals. It can be `single` or `double`.

> Default: `double`

##### `javascript.formatter.quoteProperties`

When properties inside objects should be quoted. It can be `asNeeded` or `preserve`.

> Default: `asNeeded`

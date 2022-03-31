# bail-early-buildkite-plugin

> Immediately cancel a build when any of its job fails

![Screenshot of bailed build](./.github/screenshot.png)

## Usage

1. Provide a Buildkite token with graphql and `write_builds` access via a `BUILDKITE_TOKEN` environment variable

2. Add the plugin to your steps:

```yaml
steps:
  - command: 'echo hi'
    plugins:
      - 'fast-af/bail-early#v1.2.0': ~
```

Any step using this plugin will cause the build to bail with an annotation linking to the failed job.

## Configuration

If you need to limit when the plugin is enabled, you can use the `if` parameter. Its value is eval'd in a bash conditional (e.g. `if [ <your value here> ]; then...`)

```yaml
steps:
  - command: 'echo hi'
    plugins:
      - 'fast-af/bail-early#v1.2.0':
        if: '"$SHOULD_BAIL_EARLY" = "true"'
```

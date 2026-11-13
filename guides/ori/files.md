> ## Documentation Index
> Fetch the complete documentation index at: https://openrouter.ai/docs/llms.txt
> Use this file to discover all available pages before exploring further.

# File Writing

> Find the files and directories that Ori creates during a run

Ori can write files in the workspace, in your home directory, and in the system temporary directory. The exact files depend on the command you run.

## Workspace files

When you run Ori from a project, it creates `.ori/` inside the current workspace:

```text theme={null}
<cwd>/.ori/
```

The `.ori/logs/` directory contains event logs and session transcripts. These files can include repository content and prompt text. Treat them as private data.

Add `.ori/` to your repository's `.gitignore`. This keeps private logs and transcripts out of Git.

You can delete old logs and other workspace cache files when you do not need them. Do not delete files that you are using for an active run.

## Global files

Ori uses this directory for data shared by commands and workspaces:

```text theme={null}
~/.ori/
```

It can contain downloaded templates, installed dependencies, caches, `config.json`, and `telemetry.json`. Templates, dependencies, and caches can be deleted when you want Ori to download them again. Keep `config.json` if you want to keep your settings. Delete `telemetry.json` only if you do not need the local telemetry state.

## Session history

Ori keeps the history of each built-in harness session so you can resume it. A session stays resumable for 30 days after its last turn, and Ori removes older history. To change the window, set `ORI_SESSION_HISTORY_RETENTION_DAYS` to a number of days. See the [settings reference](configuration.md#files).

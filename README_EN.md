# @aphroditee666/dsh-best-sidebar

A VSCode-like right sidebar for DeepSeek Harness (file tree / editor / terminal / git / browser), forked from [`dsh-better-sidebar`](https://github.com/omdsh-dev/DSH-better-sidebar) with built-in extra patches (already applied to the shipped `lib/` build):

1. **Silent auto-refresh file tree** — polls visible levels every 2s with signature comparison, re-renders only when content actually changed (no flickering); pauses when the tab is hidden.
2. **Right-click new folder / new file** — create a folder or empty file under any tree folder (or the workspace root), then auto-refresh. (Adds a host `fs.createDirectory` API.)
3. **Drag file into the conversation composer** — drop a sidebar file/folder onto the chat textarea to insert its **absolute path at the caret** (no `@` prefix; replaces the current selection; caret lands right after the path).

## Install

```sh
dsh plugin --profile web add @aphroditee666/dsh-best-sidebar
```

Restart the web profile afterwards (`dsh web`).

The shipped `lib/` already contains the patches; `src/` is the upstream source. Rebuilding from `src` will drop the patches — do not rebuild; edit the shipped `lib/` artifacts and repack instead.

## License

MIT (upstream dsh-better-sidebar is MIT too).
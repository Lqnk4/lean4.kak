# lean4.kak

This is a brand new project, features and dependencies are subject to change.

## Dependencies

* `kakoune-lsp` - version `18.2.0-snapshot` https://github.com/kakoune-lsp/kakoune-lsp
* `python3`

## Features
* LSP Features - handled automatically by `kakoune-lsp`
* Infoview - lean goal information goes to infoview buffers
* LaTeX Input - modify `abbreviations.json` for custom abbreviations
* Syntax Highlighting - minimal regex highlighting to pair with lsp semantic tokens

## Install
Make sure to setup kak-lsp before sourcing `lean4.kak`.

Source `lean4.kak` in your kakrc and keep both `lean4-replace-abbreviations.py` and `abbreviations.json` in your config directory.

## Semantic Tokens
To use semantic tokens, add the following to your `kakrc`.
```
hook global WinSetOption filetype=lean %{
    hook window -group lean4-semantic-tokens BufReload .* lsp-semantic-tokens
    hook window -group lean4-semantic-tokens NormalIdle .* lsp-semantic-tokens
    hook window -group lean4-semantic-tokens InsertIdle .* lsp-semantic-tokens
}
```

## Hide Cursor in Infoview
To make the cursor transparent in the infoview buffers, add the following to your `kakrc`.
```
hook global WinSetOption filetype=lean-goals %{
    set-face window PrimaryCursor Default
    set-face window PrimaryCursorEol Default
}
```

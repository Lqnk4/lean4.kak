# lean4.kak

## Dependencies

* `kakoune-lsp`
* `python3`

## Features
* Infoview - Lean goal information goes to an infoview buffer
* Unicode Input - Expands abbreviations with a python script. Modify `abbreviations.json` for custom abbreviations
* Syntax Highlighting - Minimal regex highlighting paired with lsp semantic tokens

## Install
Setup kak-lsp before sourcing `lean4.kak`.
Keep both `lean4-expand-abbrevs.py` and `abbreviations.json` in your config directory.

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

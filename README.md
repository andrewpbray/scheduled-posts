# Scheduled-posts Extension For Quarto

Allows blog posts (or any website documents) to be published according to a schedule. *Note: this extension is still in development phase and isn't yet working as planned.*

## Installing

```bash
quarto install extension andrewpbray/scheduled-posts
```

This will install the extension under the `_extensions` subdirectory.
If you're using version control, you will want to check in this directory.

## Using

This filter adds `draft: true` to the document metadata if the `date` field is in the future. This can be used to schedule posts for a blog or any type of document

More specifically, the `date` field on the document is compared to the system time on the computer that renders document. Both are in the Unix time format, so it necessary than `data-format: "X"` is used either within the metadata of the document itself or in `_quarto.yml`.

## Example

Here is the source code for a minimal example: [example.qmd](example.qmd).

Because the `date` field of this document's metadata is in the future (assuming you render it before the year 2050), the filter will add `draft: true` into the metadata. You can see this by running the following at the terminal.

```bash
quarto render example.qmd --to native
```

The result is Pandoc's AST representation of the document, the [native format](https://quarto.org/docs/extensions/lua.html#native-format). `draft: true` shows up encoded as:

```
( "draft" , MetaBool True )
```
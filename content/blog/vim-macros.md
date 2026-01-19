+++
title = "Editing an Existing Vim Macro"
template = "blog-post.html"

[extra]
name = "Darshan Kathiriya"
+++

You do not need to re-record a macro when it is almost correct. You can edit the recorded keystrokes directly and keep the same register.

## Scenario
You recorded a macro that works only if you manually move to the start of the line first. Rather than re-record it, add the missing `^` into the stored macro.

## Method 1: Paste, edit, yank back
This is the most readable option when you want to see the macro as text.

1. Put the macro into the buffer (example: register `q`):

```
"qp
```

2. Edit the line like normal text (e.g., insert `^` at the front):

```
I^
```

3. Yank the updated line back into the same register:

```
"qyy
```

4. Delete the temporary line:

```
dd
```

## Method 2: Edit the register inline
This is faster for tiny fixes.

1. Start editing the register value:

```
:let @q='
```

2. Insert the current macro contents:

```
<C-r><C-r>q
```

3. Make your change, close the quote, and press Enter.

## Quick reminders
- Record: `q{register}` … `q`
- Play back: `@{register}`
- Inspect: `:reg {register}`

## Tips
- Use `<C-v>` to insert literal special keys when editing by hand.
- Avoid using the same register for yanks/deletes while you are tweaking a macro.

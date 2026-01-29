# ASCII Mockup for LLMs

A markdown-like syntax for generating ASCII art UI mockups with AI.

## Why?

LLMs work best with text. This syntax lets you describe UI screens in a few lines and get consistent ASCII art output. No image generation, no design tools—just text in, text out.

## Usage

1. Download [ascii-mockup-llm.txt](ascii-mockup-llm.txt)
2. Attach it to your AI chat
3. Write your mockup using the syntax below
4. Get ASCII art output

## Quick Example

**Input:**
```
# Login

> Email *
> Password *

<Login>

[Forgot Password?]
```

**Output:**
```
╔══════════════════════════════════════════════════════════╗
║                                                          ║
║  ┃ Login                                                 ║
║                                                          ║
║  Email *                                                 ║
║  [__________________________________________________]    ║
║                                                          ║
║  Password *                                              ║
║  [__________________________________________________]    ║
║                                                          ║
║  ╔════════════╗                                          ║
║  ║  Login     ║                                          ║
║  ╚════════════╝                                          ║
║                                                          ║
║  Forgot Password?                                        ║
║  ‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾                                        ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝
```

## Syntax Reference

### Screen Border
```
(default)    Double border ╔═══╗
|-|          Single border ┌───┐
```

### Headings
```
# Title      ┃ Title
## Title     ┃┃ Title (+ blank line after)
### Title    ┃┃┃ Title (+ blank line after)
:: Label     Label: (group label for radio/checkbox)
```

### Input Fields
```
> Label      Text input
> Label *    Required field
>> Label     Textarea (2 rows)
>>> Label    Textarea (3 rows)
```

### Selection
```
( ) Option   Radio unchecked
(.) Option   Radio selected
[ ] Option   Checkbox unchecked
[x] Option   Checkbox checked
{} Label     Dropdown (empty)
{"val"} Label   Dropdown (with selected value)
```

### Grid Layout
```
> Field1 | > Field2    Side by side inputs
( ) A | ( ) B | ( ) C  Horizontal radio buttons
[ ] A | [ ] B          Horizontal checkboxes
```

### Buttons
```
<Button>     Primary button (double border)
<<Button>>   Secondary button (single border)
```

### Other Elements
```
[Link Text]  Underlined link
- Item       List item (• bullet)
---          Thin divider line
===          Thick divider line
```

### Messages
```
++ Message   Success [+]
-- Message   Error [-]
!! Message   Warning [!]
** Message   Info [*]
```

Messages directly after an input (no blank line) are validation messages for that field.

### Disabled States
```
~> Label     Disabled input (░░░ filled)
~<Button>    Disabled button (dotted border)
```

### Tables
```
| Col1 | Col2 | Col3 |              Basic table
| - [ ] | Name | - <Edit> |         Checkbox + button columns
| Name | Email - [url] |            Link column
##Paginator##                       Adds pagination below table
```

Column modifiers:
- `- [ ]` — Checkbox column (no header)
- `- <Btn>` — Button column (no header)  
- `Col - [url]` — Values are links


## Example Prompt

Once you attach the reference file to your AI chat, you can write prompts like this:

```
Draw this screen:

# User Management

> Search Users

| - [ ] | Name | Email - [user?id=] | Status | - <Edit><Delete> |
##Paginator##
```

The AI will generate:

```
╔══════════════════════════════════════════════════════════╗
║                                                          ║
║  ┃ User Management                                       ║
║                                                          ║
║  Search Users                                            ║
║  [__________________________________________________]    ║
║                                                          ║
║  ┌───┬────────────┬──────────────────┬────────┬────────┐ ║
║  │   │ Name       │ Email            │ Status │        │ ║
║  ├───┼────────────┼──────────────────┼────────┼────────┤ ║
║  │[ ]│            │ ______________   │        │<Edit>  │ ║
║  │   │            │ ‾‾‾‾‾‾‾‾‾‾‾‾‾‾   │        │<Delete>│ ║
║  ├───┼────────────┼──────────────────┼────────┼────────┤ ║
║  │[ ]│            │ ______________   │        │<Edit>  │ ║
║  │   │            │ ‾‾‾‾‾‾‾‾‾‾‾‾‾‾   │        │<Delete>│ ║
║  └───┴────────────┴──────────────────┴────────┴────────┘ ║
║  <<  <  [1]  2  3  >  >>                                 ║
║                                                          ║
╚══════════════════════════════════════════════════════════╝
```

## Feedback

Found a bug? Have a suggestion? [Open an issue](https://github.com/serchimed/ascii-mockup-llm-txt/issues).

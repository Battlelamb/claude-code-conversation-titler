# conversation-labeler

A [Claude Code](https://code.claude.com) skill that generates rich, well-formatted **titles** for your current conversation - so you can find it later by date and topic. It is **interactive**: it asks how you want the title (language, length, date position, style), then produces matching variants, plus a short description and tags, and a ready-to-paste `/rename` command.

It is **suggestion-only**: it never edits your session or its stored title. You apply the title you like in one step.

## Why

Claude Code auto-generates conversation titles that are generic and hard to scan later. This skill turns the current conversation into a title you actually want - long or short, dated or not, in your own language, English, or Chinese - and hands you the exact `/rename` line to apply it.

## Install

### As a plugin (recommended)

```
/plugin marketplace add Battlelamb/conversation-labeler
/plugin install conversation-labeler@conversation-labeler
```

Update later with `/plugin marketplace update conversation-labeler`.

### As a standalone skill

Copy the skill folder into your personal skills directory:

```
plugins/conversation-labeler/skills/conversation-labeler/   ->   ~/.claude/skills/conversation-labeler/
```

## Usage

Invoke it and answer the prompts:

```
/conversation-labeler
```

Or just say things like "name this chat" or "suggest a title". If you already know what you want, pass it inline to skip the questions:

```
/conversation-labeler short english slug
```

You get several variants (long / medium / short, dated / undated, slug, keyword, emoji, ...), a short description, tags, and a `/rename <title>` line. Pick the one you like and apply it.

## How it works

1. Reads the current conversation from context.
2. Asks once for language / length / date / style preferences - unless you already specified them inline.
3. Produces the matching title variants + description + tags.
4. Gives a copy-ready `/rename` command. Applying the title is your one manual step - the app owns the title, so the skill never touches the transcript.

### Why not apply the title automatically?

Claude Code manages the conversation title itself (it stores an `ai-title` and regenerates it; `/rename` writes a `customTitle` that wins). A skill cannot reliably set it, and editing the live transcript is fragile. So this skill stops at generating the name and giving you the `/rename` line - clean and safe.

## Language support

Titles can be produced in your **conversation's own language** (auto-detected), **English (EN)**, or **Chinese (CHN)** - pick one or several.

## License

[MIT](LICENSE)

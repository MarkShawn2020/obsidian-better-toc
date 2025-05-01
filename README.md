# obsidian-better-toc

Create a better table of contents for Obsidian notes.

![Example of content creation](example.gif)

## Features

This plugin exposes the following commands:

| Action                                          | Hotkey           |
| ----------------------------------------------- | ---------------- |
| Create full table of contents                   | Blank by default |
| Create table of contents for next heading level | Blank by default |

And the following settings:

| Setting              | type                 | Default    |
| -------------------- | -------------------- | ---------- |
| List Style           | 'bullet' or 'number' | 'bullet'   |
| Title                | 'string'             | undefined' |
| Minimum header depth | number               | 2          |
| Maximum header depth | number               | 6          |

## Usage

This plugin will create a table of content for the sub-heading of the current heading level.

**Example:**

_Input:_ Run "Table of Contents" under a level 2 heading  
_Output:_ "Table of Contents" only contains subheadings of that level 2 heading

## Installing

Either install the latest release from Obsidian directly or unzip the latest release into your `<vault>/.obsidian/plugins/` folder.

Once the plugin is installed, you need to make sure that the switch for "Table of Contents" is turned on.
After you are all setup you would see this plugins commands in the command palette (`CMD + P`).
You can assign the commands to hotkeys for easy usage.

Here is my setup:

- Create full table of contents => `CMD + SHIFT + T`
- Create table of contents for next heading level => `CMD + T`

## Customizations

### Detailed Nested Ordered Lists

If you want the table of contents to use nested list counting (ex: 1.1, 1.2) add the following CSS snippet to obsidian.
This will effect all ordered lists in your notes.

```css
ol {
  counter-reset: item;
}

ol li {
  display: block;
}

ol li:before {
  content: counters(item, ".") ". ";
  counter-increment: item;
  padding-right: 5px;
}
```

> NOTE: Make sure you enable the snippet in obsidian's options.

## Development

### Build Setup

This plugin uses a modern build setup with esbuild:

```bash
# Install dependencies
pnpm install

# Start development server with hot reload
pnpm dev

# Build for production
pnpm build
```

### Build System Notes

The build system was modernized to use direct esbuild configuration rather than the legacy obsidian-plugin-cli. This resolves compatibility issues with newer Node.js versions and dependencies.

The changes include:

1. Custom `esbuild.config.mjs` for bundling
2. Updated build scripts in package.json
3. Dependency updates for compatibility with current Obsidian API

### Obsidian API Compatibility

This plugin has been updated to work with the current Obsidian API. Legacy code referencing deprecated API elements like `sourceMode.cmEditor` has been updated to use the current `editor` property.

## Why Choose obsidian-better-toc?

This plugin is a modernized fork of the original `obsidian-plugin-toc` with several key improvements:

1. **Modern Build System**: Uses the latest esbuild configuration for better compatibility with current Node.js versions.

2. **Updated API Compatibility**: Works with the latest Obsidian API, fixing deprecated code patterns that could break functionality.

3. **Active Maintenance**: Regularly updated to ensure compatibility with the latest Obsidian releases.

4. **Performance Optimizations**: Improved code structure for better performance and reliability.

5. **Future Enhancements**: Planned improvements include automatic TOC updates, custom styling options, and more flexible configuration.

If you've experienced issues with the original TOC plugin or want a more reliable and future-proof solution, `obsidian-better-toc` is the right choice for you.
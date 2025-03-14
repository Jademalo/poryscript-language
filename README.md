# Poryscript Language Extension

This is a basic language extension for Poryscript. (https://github.com/huderlem/poryscript)

At this basic stage it supports basic Syntax Highlighting

## Configuration

The extension parses files like `event.inc` and `movement.inc` to provide completion hints on your LSP client. (Visual Studio Code)
It needs to know where those files are with respect to your root workspace. To do so, it reads the property `languageServerPoryscript.commandIncludes` of your `settings.json`.
If the field is not set it defaults to the following setting:

```json
{
    "languageServerPoryscript.commandIncludes": [
        "asm/macros/event.inc",
        "asm/macros/movement.inc"
    ]
}
```

The extension also parses customizable files to read values usually present when working with `poryscript`. A few are included in the default settings, but new ones can be configured or changed at will. Each entry contains a regular `expression`, a type which can be `special` or `define` and a `file` path. The first match group of the regular expression will be treated as the name of the defined token. The second group will be treated as a detail in the completion hint window. The default settings are:

```json
    "languageServerPoryscript.symbolIncludes": [
    
        {
            "expression": "^\\s*def_special\\s+(\\w+)",
            "type": "special",
            "file": "data/specials.inc"
        },
        {
            "expression": "^\\s*#define\\s+(FLAG_\\w+)\\s+(.+)",
            "type": "define",
            "file": "include/constants/flags.h"
        },
        {
            "expression": "^\\s*#define\\s+(VAR_\\w+)\\s+(.+)",
            "type": "define",
            "file": "include/constants/vars.h"
        },
        {
            "expression": "^\\s*#define\\s+(ITEM_\\w+)\\s+(.+)",
            "type": "define",
            "file": "include/constants/items.h"
        },
        {
            "expression": "^\\s*#define\\s+(SE_\\w+)\\s+(.+)",
            "type": "define",
            "file": "include/constants/songs.h"
        },
        {
            "expression": "^\\s*#define\\s+(MUS_\\w+)\\s+(.+)",
            "type": "define",
            "file": "include/constants/songs.h"
        },
        {
            "expression": "^\\s*#define\\s+(MAP_SCRIPT_\\w+)\\s+(.+)",
            "type": "define",
            "file": "include/constants/map_scripts.h"
        }
    ]
```

## Requirements

* Visual Studio Code ^1.44.0

## Known Issues

* Extension settings are read relatively to your root workpace, therefore this does not work in a multi-workspace environment.

## Release Notes

Please view the [CHANGELOG](CHANGELOG.md) for a full list of changes.

### 2.2.1

* Fixed broken windows paths for `readfs`client commands
* npm audit fix

### 2.2.0

* Added Completion hints and highlighting for symbols from other script files
* Added Completion hints and highlighting for custom includable files
* Added Definition Lookup Provider
* Added Icon

### 2.1.0

* Several fixes in highlighting and semantic highlighting
* Semantic highlighting for document local constants

### 2.0.0

* Experimental Semantic Highlighter

### 1.5.1

* Minor fixes and improvements

### 1.5.0

* Add constant parsing

### 1.4.1

* Minor bugfixes

### 1.4.0

* Added `poryswitch` as a completion hint
* Major bug fixes for most non-unix platforms

### 1.3.0

* Added language server capabilities

### 1.2.0

* Added Symbol name declarations to entity.name.function.pory

### 1.1.0

* Minor Fixes and Improvements.

### 1.0.0

* Initial release, support basic syntax highlighting

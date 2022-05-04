<img src="assets/Banner.png" width="100%">

# Diplo Language
---

# Interpreter usage

Use the ```diplo``` command to execute your program.

By convention, Diplo scripts have ```.diplo``` file extension, but **Diplo Interpreter** can parse files with any extensions.

```
diplo <File> [ConfigFlags]
```

- With ```File``` an absolute or relative file path.
- With ```ConfigFlags``` letters string. See [Config Flags](#config-flags) letters.

## Example

```
diplo HelloWorld.diplo et
```

# Config flags

Config flags are used to configure execution behavior.

## List
- ```e```: Exit program without waiting for a keypress.
- ```t```: Exit program displaying execution time.
- ```d```: Enable debug.
# viccuad's dotfiles

My dotfiles!

![example](https://github.com/viccuad/dotfiles/raw/master/example.png)

## install/uninstall

To install run this:

```
sh
git clone https://github.com/viccuad/dotfiles.git ~/.dotfiles
cd ~/.dotfiles
./install.sh
```
The install script will ask if you want to set your Zsh as the default
shell, make a new gitconfig, make a dry run that does not write
anything, etc.
Installing a dir will symlink the appropriate files in `.dotfiles` to your 
home directory. Everything is configured and tweaked within `~/.dotfiles`. 

We are using stow, and stow _does_ _not_ delete or overwrite file that 
already exist. You will need to make a backup of them or delete them.

## uninstall

To uninstall run:

```
./uninstall.sh
```

## topical

Everything's built around topic areas. If you're adding a new area to your
forked dotfiles — say, "Java" — you can simply add a `java` directory and put
files in there. Anything with an extension of `.zsh` inside of `java/nostow/` 
will get automatically included into your shell. All the things inside `java`
that aren't inside of `nostow` or don't have `nostow` in their filenames
will get symlinked into `$HOME` when you run `install.sh`.

## components

There's a few special files in the hierarchy.

- **/nostow/bin/**: Anything in `bin/` will get added to your `$PATH` and be made
  available everywhere.
- **topic/nostow/*.zsh**: Any files ending in `.zsh` get loaded into your
  environment.
- **topic/nostow/path.zsh**: Any file named `path.zsh` is loaded first and is
  expected to setup `$PATH` or similar.
- **topic/nostow/completion.zsh**: Any file named `completion.zsh` is loaded
  last and is expected to setup autocomplete.
- **topic/**nostow**: Any files containing `nostow` will not get
	symlinked by stow. 


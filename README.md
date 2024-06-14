# How To edit [Wallpaper Engine](https://www.wallpaperengine.io/en) Wallpapers - Windows

## Download's

1. Wallpaper Engine: [Steam](https://store.steampowered.com/app/431960/Wallpaper_Engine/) (it's paid :c)
2. Download RePKG: GitHub (in this repo)

## Steps

1. [Download](https://i.imgur.com/sNy7naW.png) the wallpaper you want to edit
2. Locate the wallpaper in the Wallpaper Engine folder

```bash
C:\Program Files (x86)\Steam\steamapps\workshop\content\431960\{wallpaper_id}
```

3. Extract the wallpaper with RePKG exaple:

```bash
.\RePKG.exe extract -e tex -s -o ./output "C:\Program Files (x86)\Steam\steamapps\workshop\content\431960\{wallpaper_id}\scene.pkg"
```

4. Edit the files in the `./output` folder



# RePKG
Wallpaper engine PKG unpacker/TEX converter, written in C#.

PKG and TEX formats reverse engineered by me.

Feel free to report errors.

# Features
- Extract PKG files
- Convert PKG into wallpaper engine project
- Convert TEX to image
- Dump PKG/TEX info

### Commands
- help - shows those commands, use `help "extract"` and `help "info"` to see options for them
- extract - extracts specified PKG/TEX file, or files from folder
```
-o, --output          (Default: ./output) Output directory
-i, --ignoreexts      Don't extract files with specified extensions (delimited by comma ",")
-e, --onlyexts        Only extract files with specified extensions (delimited by comma ",")
-d, --debuginfo       Print debug info while extracting/decompiling
-t, --tex             Convert all TEX files into images from specified directory in input
-s, --singledir       Should all extracted files be put in one directory instead of their entry path
-r, --recursive       Recursive search in all subfolders of specified directory
-c, --copyproject     Copy project.json and preview.jpg from beside PKG into output directory
-n, --usename         Use name from project.json as project subfolder name instead of id
--no-tex-convert      Don't convert TEX files into images while extracting PKG
--overwrite           Overwrite all existing files
```
- info - Dumps PKG/TEX info
```
-s, --sort             Sort entries a-z
-b, --sortby           (Default: name) Sort by ... (available options: name, extension, size)
-t, --tex              Dump info about all TEX files from specified directory
-p, --projectinfo      Keys to dump from project.json (delimit using comma) (* for all)
-e, --printentries     Print entries in packages
--title-filter         Title filter
```
 
### Examples
Simply extract PKG and convert TEX entries into images to output folder created in current directory
```
repkg extract E:\Games\steamapps\workshop\content\123\scene.pkg
```
Find PKG files in subfolders of specified directory and make wallpaper engine projects out of them in output directory
```
repkg extract -c E:\Games\steamapps\workshop\content\123
```
Find PKG files in subfolders of specified directory and only convert TEX entries to png then put them in ./output omitting their paths from PKG:
```
repkg extract -e tex -s -o ./output E:\Games\steamapps\workshop\content\123
```
Convert all TEX files to images from specific folder
```
repkg extract -t -s E:\path\to\dir\with\tex\files
```

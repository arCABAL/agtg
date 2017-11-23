## Example
![helloworld](https://i.imgur.com/zDqeUvg.gif)

# arCABAL GRUB type generator for Cube 2 Sauerbraten

Script to generate text geometry in a sauerbraten map by simply typing that text into a command.
Based on cube2_typegen by Nyne. https://github.com/gitnyne/cube2_typegen.
The font used in this script is part of GNU GRUB, licensed under the GPLv3.

## FEATURES  
- both uppercase and lowercase characters
- punctuation marks
- letters with diacritics
- uppercase and lowercase cyrillic font
- compatible with Linux, Windows, and Mac OS

## INSTALLATION
### Method 1: Download and extract zip archives
  
1. Download agtg.cfg from this project and put it your sauerbraten custom content directory.

	On Linux this is ~/.sauerbraten

	On Windows 7 and 10 this is C:\Users\\\%username%\Documents\My Games\Sauerbraten

	On an Apple Mac it is most likely macHD/users/%username%/library/Application Support/sauerbraten/
	
2. Download the two folders `grubfont` and `grubfontbbg` from the linked grubfonts github project (packages @ 77efb77) and put them both inside sauerbraten/packages.

3. add the following line to your autoexec.cfg inside your sauerbraten directory:

	`exec agtg.cfg`


### Method 2: Use git.
If you want to use git instead, use the following commands:


```text
git clone https://github.com/arCABAL/agtg.git
	
cd agtg
	
git submodule init && git submodule update
```	
(Init only matters if you have a fresh clone of the repo)
	
2. Then copy agtg.cfg and packages into your sauerbraten directory and press accept if asked to confirm merging the packages folder, and also add the `exec agtg.cfg` line to your autoexec.cfg


## USAGE  

In edit mode, select the right face of a cube pointing towards one specific direction. See the included agtg.png to see which, and move back so all generated text will appear in your field of vision.

If you don't do this the generated text will be truncated to the part which can be generated in your view as you can only edit in sauerbraten on things which are inside your field of view.

You probably want to use the smallest grid size but bigger text is also possible. with the right face of the cube selected, enter this command:  

```text
/agtg Hello World!
```

As you can see, you don't need to put double quotes "" around your input. However, if you want to generate text with characters which are interpreted by cubescript, you do have to put double quotes around your input and escape some characters. Characters which mess up up the input are: ^;()[]"
You can escape these characters with a ^ in front. So for example, if you want to generate this string:  

```text 
this is a string with a ] and a ; but which can still be generated.
```

You would use:

```text 
/agtg "this is a string with a ^] and a ^; but which can still be generated"
```

These are all the characters which you can generate. I believe they are also all the characters you can type into the game but let me (arCABAL on freenode and Discord: arCABAL#6439) know if I missed any and I will add them.

```text
?1234567890!@#$%^&*()`-=~_+[]\{}|;':^",./<> ßabcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZáàäâãåčďéèëêěíìïîñňóòöôõøřšťúùüûůýÿžœæ
ÁÀÄÂÃÅČĎÉÈËÊĚÍÌÏÎÑŇÓÒÖÔÕØŘŠŤÚÙÜÛŮÝŸŽŒÆaбвгдeëжзийклмнoпpcтyфxцчшщъыьэюяґїєAБBГДEËЖЗИЙKЛMHOПPCTУФXЦЧШЩЪЫЬЭЮЯҐЇЄ 
```

Tip: you can paste text into the game using clients which use SDL2.

## FONT SELECTION

There's two fonts in the packages submodule. The first font, grubfont, is floating cubes forming the characters of the font. The second font, grubfontbbg (grub font black background), is the same font but with black cubes around them forming a background. It is generally better to use grubfont to minimalize the wtr of your map. 

you can select a font using /agtgfont nameofthefont so that is one of those two for now:

```text
/agtgfont grubfont  
/agtgfont grubfontbbg  
```

You can autocomplete the font selection with tab.


## NOTES ON ADDING YOUR OWN FONT  

If you want to add your own font, you have to add another folder to your packages folder and use the savebrush command to save each character as a .obr file.

For every character, select it and for example for the letter a, use:

```text
/savebrush yourfontname/a
```

Use the same filenames as used in grubfont and add your fontname on line 13 of agtg.cfg so agtgfont selection can tab autocomplete it.

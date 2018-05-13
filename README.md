
# arCABAL GRUB type generator for Cube 2 Sauerbraten

![helloworld](https://i.imgur.com/zDqeUvg.gif)

Script to generate text geometry in a sauerbraten map by simply typing that text into a command.
Based on cube2_typegen by Nyne. https://github.com/gitnyne/cube2_typegen.
The font used in this script is part of GNU GRUB, licensed under the GPLv3.

## Features  
- Both uppercase and lowercase characters
- Punctuation marks
- Letters with diacritics
- Uppercase and lowercase cyrillic font
- Compatible with Linux, Windows, and Mac OS

## Installation
### Method 1: Download and extract zip archives
  
1. Download agtg.cfg from this project and put it your sauerbraten custom content directory.

	On Linux this is ~/.sauerbraten

	On Windows 7 and 10 this is C:\Users\\\%username%\Documents\My Games\Sauerbraten

	On an Apple Mac it is most likely macHD/users/%username%/library/Application Support/sauerbraten/
	
2. Download the two folders `grubfont` and `grubfontbbg` from the linked grubfonts github project (packages @ 77efb77) and put them both inside sauerbraten/packages.

3. Download the folder `awesomefont` and put it inside sauerbraten/packages

4. Add the following line to your autoexec.cfg, which is inside your sauerbraten directory:

	`exec agtg.cfg`
	
If this is the first script you've wanted to add to Sauerbraten, you will not have an "autoexec.cfg" file. 
In that case, simply create a textfile called "autoexec.cfg" and paste the exec line into it.


### Method 2: Use git.
1. If you want to use git instead, use the following commands:


```text
git clone https://github.com/arCABAL/agtg.git
	
cd agtg
	
git submodule init && git submodule update
```	
(Init only matters if you have a fresh clone of the repo)
	
2. Then copy agtg.cfg and packages into your sauerbraten directory and press accept if asked to confirm merging the packages folder, copy the `awesomefont` folder into packages, and also add the `exec agtg.cfg` line to your autoexec.cfg


## Usage

In edit mode, select the right face of a cube pointing towards one specific direction. See the included agtg.png to see which, and move back so all generated text will appear in your field of view.

If you don't do this the generated text will be truncated to the part which can be generated in your view as you can only edit in sauerbraten on things which are inside your field of view.

You probably want to use the smallest grid size but bigger text is also possible with bigger grid sizes. With the right face of the cube selected, enter this command:  

```text
/agtg Hello World!
```

As you can see, you don't need to put double quotes "" around your input. However, if you want to generate text with characters which are interpreted by cubescript, you do have to put double quotes around your input and escape some characters. Characters which are part of the cubescript syntax and mess up the input are ^;()[]"  
You can escape these characters with an escape character ^ in front. So for example, if you want to generate this string:  

```text 
this is a string with a ] and a ^ but which can still be generated.
```

You would use:

```text 
/agtg "this is a string with a ^] and a ^^ but which can still be generated"
```

These are all the characters which you can generate. I believe they are also all the characters you can type into the game.

```text
?1234567890!@#$%^&*()`-=~_+[]\{}|;':^",./<>ß abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZáàäâãåčďéèëêěíìïîñňóòöôõøřšťúùüûůýÿžœæ
ÁÀÄÂÃÅČĎÉÈËÊĚÍÌÏÎÑŇÓÒÖÔÕØŘŠŤÚÙÜÛŮÝŸŽŒÆaбвгдeëжзийклмнoпpcтyфxцчшщъыьэюяґїєAБBГДEËЖЗИЙKЛMHOПPCTУФXЦЧШЩЪЫЬЭЮЯҐЇЄ 
```

Tip: you can paste text into the game using clients which use SDL2.

## Font selection

There are two fonts in the packages submodule. The default font, grubfont, consists of small floating white cubes forming the characters. The second font, grubfontbbg (grub font black background), is the same font but with black cubes around them forming a background. It is generally better to use grubfont to minimalize the wtr of your map. I've also added a font with smooth curves called 'awesomefont', in contrast to the pixelated grubfont which consists only of blocks. Awesomefont does not have the cyrillic characters.

you can select a font using /agtgfont nameofthefont so that is one of those three:

```text
/agtgfont grubfont  
/agtgfont grubfontbbg  
/agtgfont awesomefont
```

You can autocomplete the font selection with tab.


## Notes on adding your own font

if you want to add your own font, you have to add another folder to your packages folder and use the savebrush command to save each character as a .obr file. Save each character with the same naming structure as used for the other fonts. Make sure that your font's characters are oriented in the right direction when selecting and saving them as brushes in the game. Take a look at the small red cube origin, it should be at the front bottom left. 

For every character, select it and for example for the letter a use:

```text
/savebrush yourfontname/a
```

To save your uppercase A brush:

```text
/savebrush yourfontname/UPPERCASE/A_UPPER
```

Also add your fontname to the `listcomplete agtgfont` list of agtg.cfg at line 10 so that agtgfont selection can tab autocomplete it.

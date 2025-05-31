# athena-gtk
A GTK theme which attempts to mimic the monochrome look of XAW applications in GTK

This theme attempts to make GTK apps look as close as possible to being an X Athena widgets app without compromising on features such as scroll bars (although I wish I could implement the proper scrollbars).

## Complete:
* Most widgets
* Everything you would realistically need
* Selection support

## Recommended applications:
* PCManFM (gtk3)
* L3afpad
* Other GTK apps I did not mention

## To do:
* GTK 2.0 + 4.0 (GTK 2.0 will come before 4.0, but the port to 4.0 should be easy enough I guess)
* Try to figure out how to disable the on and off icons on switches
* Mouse selection backgrounds
* Sidebar in the file selector

## Installation
I recommend the following to enhance the look and feel, but doing this is completely optional:
* Misc fixed fonts (requires fonttosfnt, xorg-fonts-100dpi, and xorg-fonts-75dpi on Arch)
  * Instructions on how to do this will be below the installation process.

To install this theme, simply clone the repository and throw it into the ~/.themes/ folder, then apply it with either the ~/.config/gtk-3.0/settings.ini file, or through a GTK 2/3 GUI application such as lxappearance.

## Misc fixed font/other bitmap fonts (optional)
Since Pango 1.44, GTK has not supported traditional bitmap fonts such as those in the BDF or PCF format. Thankfully though, using a tool called fonttosfnt, this can be completely fixed, allowing you to use these fonts with GTK.

### Note:
If you have not edited your font configuration, doing it will allow this to be done. Go into either a terminal or a file manager launched under the root user, and delete `/etc/fonts/conf.d/70-no-bitmaps.conf`. After that is done, you may need to either log out, restart X11, or possibly restart your computer.

Going back to getting these fonts to work with GTK, open a terminal under the root user (or with normal privileges, but not recommended for this), and save the following somewhere:

``mkdir -p /home/$USER/.fonts/
sudo sed -i 's/FAMILY_NAME.*/FAMILY_NAME "Fixed"/' $1x$2.pcf.gz
sudo fonttosfnt -b -c -g 2 -m 2 -o $1x$2.otb $1x$2.pcf.gz
sudo mv $1x$2.otb /home/$USER/.fonts/``

NOTE: If you are using a different font family, replace Fixed in quotes on the second line with whatever the font family you're using is. Not doing this will result in random font conflicts.

Then after the file is saved, run `chmod +x <FILE>`, in the directory the file you wrote it to is in (it can done anywhere too, but you have to list the fully directory path). This will allow the file to be executed.

After that is done, replace Fixed with whatever family you plan to use. If you're doing this with multiple fonts, it's advised that you change the last line of the file to move it to the directory with a unique name (ex. terminus-$1x$2.otb).

Once all of that is done, simply cd to the directory where the font you want is located (misc fixed is under /usr/share/fonts/misc/), and type in the width and height of the font as both the first and second arguments respectively (so if the script is located in the home directory with the name script.sh and the font resolution is 4x6, ~/script.sh 4 6). For the Misc Fixed font, you will likely want the 6x13 variant.

**WARNING:** 
You can have multiple sizes of your font, but if a size has an equal vertical size to one another, the biggest font horizontally will take priority. The only way to get past this is by moving the fonts you don't want to a different directory. On top of that, in GTK itself, font variants like bold, italic, and semicondensed will not display properly, so sticking with regular is the only solution.

With all of this done now, you should be able to select Fixed or whatever font you want in the font selector!

## Classic X11 cursors (X11 only, optional)
With this theme and the font, you might want to go even further with the classic X11 style. This will further enhance it, but with the cost of being a bit destructive.

To do this, simply delete everything inside index.theme in /usr/share/icons/default, and go into ~/.icons/ or ~/.local/share/icons. If the default cursor theme is there in either of those places, do the same.

Setting the cursor theme should be as simple as going into whatever theme panel you have (or going into the settings.ini file) and setting it to blank or default, but if whatever application you're using doesn't like that, use LXAppearance instead. Now you should have the true classic X11 cursors.

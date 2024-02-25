# ROOT without Xcode

I know what you are thinking: is that possible? Aw man I hate Xcode, they occupied all my free storage! Here's a way (that worked for me) to use ROOT without Xcode.

I still don't know is if by just unistalling the application Xcode you automatically free al the space it used to occupy. 
Yet by opening Settings and looking for the Developer folder try removing project build caches and then uninstall the Xcode app.
It mandatory to install CMake in onder to do all these things. If you don't know how to install CMake on your Mac why don't you look at my MacOS set-up guide? 

If you have already insalled ROOT I suggest that you remove il completely by opening the Terminal and typing

```zsh
% rm -rf root* 
```

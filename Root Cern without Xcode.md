# ROOT without Xcode

I know what you are thinking: is that possible? Aw man I hate Xcode, they occupied all my free storage! Here's a way (that worked for me) to use ROOT without Xcode.

A little disclaimer: I have a Mac from mid 2013, the one with the old processor (before M1). Everything has worked fine for me, if some of you have a newer Mac and these intructions don't work with you, feel free to contact me. I may not know how to fix your problems but I may know who might!

I still don't know if by just uninstalling the application Xcode you automatically free al the space it used to occupy. 
Yet, by opening Settings and looking for the Developer folder, try to remove project build caches and then uninstall the Xcode app.
It mandatory to install CMake in onder to do all these things. If you don't know how to install CMake on your Mac why don't you look at my MacOS set-up guide? -> https://github.com/vero-dav-vero/here-to-help/blob/main/MacOS%20set-up :)

If you have already installed ROOT I suggest that you remove it completely by opening the Terminal and typing

```zsh
% rm -rf root* 
```
Then type

```zsh
% git clone --branch latest-stable --depth=1 https://github.com/root-project/root.git root_src 
```
and then

```zsh
% mkdir root_build root_install && cd root_build
```

then

```zsh
% cmake -DCMAKE_INSTALL_PREFIX=../root_install ../root_src
```
and check CMake configuration output for warnings or errors. Then type

```zsh
% cmake --build . -- install -j4 
```
if you have the M1 or M2 processor use -j6, the computer may become "a little bit" hot. This is the part that took the long. Just plug in your Mac and wait. Be patient because it's going to take a "while".

After you type this

```zsh
% source ../root_install/bin/thisroot.sh
```

you are able to open and use ROOT.

> **PAY ATTENTION**
> 
> Every time you close the Terminal app you _need_ to go to the **root_build** folder
> ```zsh
> % cd root_build
> ```
>
> and then type this
> 
> ```zsh
> % source ../root_install/bin/thisroot.sh
> ```
>
> Only _after_ this procedure you may open ROOT
>
> ```zsh
> % root
> ```
> 
> What happens if you forget? Easy! ROOT doesn't work.









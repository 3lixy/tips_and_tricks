# PuTTY


##### Delete key for csh and bash shells

For the Bourne Shell, add the following lines to your .shrc. See sh(1) and editrc(5).
bind ^? ed-delete-next-char # for console
bind ^[[3~ ed-delete-next-char # for xterm

For the C Shell, add the following lines to your .cshrc. See csh(1).
bindkey ^? delete-char # for console
bindkey ^[[3~ delete-char # for xterm

##### Numpad

Click the PuTTY icon in the upper-left corner of the window. From the drop-down menu, click Change Settings.
Click Terminal, and then click Features.
Under "Enabling and disabling advanced terminal features", check Disable application keypad mode.
Click Apply.
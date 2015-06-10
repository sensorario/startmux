# ttmux

A script that make easy tmux configuration bootstrap of a project

## Add your own custom configuration

To add a custom configuration, it's necessary to create a file with extension .ttmux. When loaded, ttmux select the right file by asking which one the user want to load.

## Order your windows

Associative arrays, in bash, are not sortable.

## Example

Here an example. Windows will be opened with the order in the list. `first` parameter, is the name of the window. `second` parameter, is the command appended on that window.

    #!/bin/bash
    declare -A combo=()
    combo+=([home]='cd ~')
    combo+=([logs]='cd /var/log')

## Windows order

Associative array, in bash, are not ordered. To customize the order of windows, add another array to configuration like this:

    #!/bin/bash
    echo ""
    echo "You are loading default configuration"
    declare -A combo=()
    combo+=([logs]='cd /var/log; clear; pwd')
    combo+=([home]='cd ~; clear; pwd')
    order=(home logs)

## Execute tmux from everywhere

To make ttmux executable from everywhere, add a symbolic link your /usr/local/bin folder

    # cd /usr/local/bin
    # ln -s ~/path/to/sensorario/ttmux/ttmux .

## Run command with configuration file

There is also possibility to run ttmux with configuration file as parameter

    $ ttmux filename.ttmux

## Configure ttmux to open windows in same branch

This is good. Because I can configure 7/8 different windows and open all of them in the same branch.

    #!/bin/bash
    branch='master'
    declare -A combo=()
    combo+=([legacy]="cd /path/to/folder; git checkout ${branch}; clear; pwd")
    combo+=([ultimate]="cd /path/to/another/folder; git checkout ${branch}; clear; pwd")
    order=( legacy ultimate )

## How to split a pane vertically

In some scenario, I need an additional vertical pane, maybe to see phplog or something like that. Add an additional pane on ttmux is easy: we need to add an associative array with only the name of the window name.

    declare -A panes=()
    panes+=([ultimate]=)




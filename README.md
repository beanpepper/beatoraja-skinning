# beatoraja-skinning
A work-in-progress english documentation for skinning in beatoraja
(Huge thanks to Mr. Mary for helping out with some definitions)

# Preamble
Dont expect this to end up being fully fledged, all encompassing, or even complete. I am
a novice in many aspects, so please feel free to correct me or pull request to fix any mistakes.
Also im doing this mostly for myself, so i may end up abandoning it if something else catches
my interest.

# Overview
Beatoraja will automatically seek out the following files in the folder of a skin:
	decide.luaskin
	more to be added

the following code is written in every single .luaskin file

	local t = require( "[PATH TO LUA FILE]" )
	if skin_config then
		return t.main()
	else
		return t.header
	end

do note that the path uses "." instead of \, and that the ".lua" is not specified
ie: require("lua.decide.decidemain")


the .luaskin seems to be loading and passing the main() function defined on the separate file
and returns it to be used by the game, while also passing a "header" which is a table filled with data.
In this case, you are defining stuff as code and then it gets run automatically, so to create and modify visuals you have to understand:

* what it looks for
* how to define assets

The header is where all information goes. If you're familiar with LR2 you can think of it as the place where you define every single element. For example, something like `#STARTINPUT` would be defined as `input = [whaever value you wanna define it as]`.

Here is an example of what that looks like, courtesy of Mr. Mary:
```lua
local header = {
    type = 0,
    name = "PIZDO DYSK TYSIONC",
    w = 1920,
    h = 1080,
    loadend = 3000,
    playstart = 1500,
    scene = 3600000,
    input = 500,
    close = 1000,
    fadeout = 100,
    property = {
        {name = "Playside", def = "Left", item = {
            {name = "Left", op = 910},
            {name = "Right", op = 911},
        }},
    },
    filepath = {
        {name = "judge", path = "judge/*.png"},
        {name = "bomb", path = "bomb/*.png"},
        {name = "pomyuchara", path = "pomyu/*"}
    },
    offset = {}
}
```
This is both helful yet somewhat annoying as it carries over the simplicity of skinning from LR2 to beatoraja, the downside being that you must define everything as tables, and you have to automate some parts of it with code. This is both obnoxious to do as a beginner and a total nightmare to read for anyone else.

Either way, we have a lot of work done for us already! you can check out the [LR2 skinhelp page](https://right-stick.sub.jp/lr2skinhelp.html) to figure out different parts. It is still all in japanese and could be cumbersome to go through, but that's what this guide is for!
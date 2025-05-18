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

	(do note that the path uses "." instead of \, and that the ".lua" is not specified
	ie: require( "lua.decide.decidemain" )


the .luaskin seems to be loading and passing the main() function defined on the separate file
and returns it to be used by the game, while also passing a "header" which is a struct filled with data.
In this case, you are defining stuff as code and then it gets run automatically, so to create and modify visuals you have to understand:

	> what it looks for
	> how to define assets

As for the header, you can define the following values to it:

	type = what the skin is for
		7KEYS, decide, etc.
	
	name 		= name of the skin
	w			= width resolution
	h			= height resolution
	loadend		= Minimum ammount of milliseconds between loading the skin and getting on the "playready" state
	playstart	= the minimum ammount of milliseconds that the skin has to wait between starting the "playready" state and actually playing
	scene		= unknown, keep at "3600000"
	input		= the ammount of milliseconds that it takes for the skin to start accepting inputs
	close		= how many milliseconds pass when you "fail" a chart before continuing
	fadeout		= how many milliseconds pass when you "finish" a chart before continuing
	category	= unknown
	property	= table of options
	filepath	= table of paths for resources, such as images, videos, etc.

An example of a header (courtesy of Mr. Mary) would be as follows:

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




header
function main()

important files????:


????
skintype
what file inits everything


???
whenever defining a toggleable property, it is/ds/hgpdfes,alhoapetjnmpfdtearnh oiklmnparhtgfnjijkmnopshnrtiklpjmno
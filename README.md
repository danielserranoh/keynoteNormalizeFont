# keynoteNormalizeFont
An apple script to set all fonts in a keynote document to de defined font

Keynote by apple used to have a way to change the fonts defined in the keynote but not present in the system. Since version 5, when apple changed the underlying technology to share keynote with iOS and iCloud versions of the software, Keynote has no longer this essential feature.

It is not possible to change the font in a document is an easy way. Here is where this script becomes handy.

Essentially, the script goes throut all the text elements and changes the font to a predefined font. Hence the name of the Script, as all the different fonts will be converted to the defined font. All the fonts of all the scriptable objects.

This is the script in Apple Script:


-- Define the new font
set newFont to "InsertYourFontHere"
  -- The font name must be the name of the font as shown in the Font Book App

--check if Keynote is running
if running of application "Keynote" is true then
	
	tell application "Keynote"
		tell the front document
			-- Change the font of the text item of every master slide to newFont
			set numberOfMasterSlides to the number of master slides
			repeat with thisMasterSlideNumber from 1 to numberOfMasterSlides
				tell master slide thisMasterSlideNumber
					-- set the font of the object text of every iWork container containing a font to newFont
					set the font of the object text of every text item to newFont
					set the font of the object text of every shape to newFont
					set the font of the object text of the default title item to newFont
					set the font of the object text of the default body item to newFont
					set the font name of the range of every table to newFont
				end tell
			end repeat
		end tell
	end tell
end if



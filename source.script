using terms from application "Mail"
	on perform mail action with messages theseMessages for rule SaveSender
		say "Dodawanie nowych kontaktów do aplikacji"
		set mcount to count of theseMessages
		say "Ilość to " & mcount
		repeat with theMessage in theseMessages
			set name_ to extract name from sender of theMessage
			set nameArray to my split(name_, " ")
			set theFirstName to item 1 of nameArray
			set theLastName to last item of nameArray
			set email_ to extract address from sender of theMessage
			-- say "Dodaję " & theFirstName & " " & theLastName
			tell application "Contacts"
				if not (exists (1st person whose first name is theFirstName and last name is theLastName and value of every email contains email_)) then
					set thePerson to make new person with properties {first name:theFirstName, last name:theLastName}
					make new email at end of every email of thePerson with properties {label:"Praca", value:email_}
				end if
				save
			end tell
		end repeat
		tell me to say "Zakończono dodawanie"
	end perform mail action with messages
end using terms from


on split(theString, theDelimiter)
	set oldDelimiters to AppleScript's text item delimiters
	set AppleScript's text item delimiters to theDelimiter
	set theArray to every text item of theString
	set AppleScript's text item delimiters to oldDelimiters
	return theArray
end split

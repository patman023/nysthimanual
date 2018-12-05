# Template/Styleguide for NYSTHI Manpages

Intended for use in a monospace text editor such as Notepad++. If you need to copypaste off of Github, click the "Raw" button just above and to the right of this section of the page. That way you don't strip the Markdown formatting or add extra HTML crap.

	If a *, #, or ` looks out of place to you, but you're not well-versed in Github-Flavoured Markdown syntax, just leave it be ;-) 
	-Pat
==========

# (Name of Module)

Author: (Your Name(s); github handles are okay here, as are Proper Names and initials, ie. John D., J. Doe)

Last Updated: YYYY/MM/DD

Last Patch: 0.6.33

**INDEX** (If you can't get this working on your own, just let Pat know. At least try to keep the general formatting.)

1. [Antonio Says](#antonio-says)
2. [Basics](#basics)
3. [Functions by Section](#functions-by-section)
   - [Section A](#section-a)
   - [Section B](#section-b)
   - [Section C](#section-c)
   - [Section D](#section-d)
4. [Usage](#usage)
5. [Sample Patches](#sample-patches)

## Antonio Says

```
	0.6.33
COPY PASTE THE RELEVANT PATCHNOTES FROM THE LATEST PARSED CHANGELOG BETWEEN THE TICKMARKS

	0.666.antonio.works.way.too.fast
If it looks wonky, try a
    nd clean up 
------- extra spaces, 
------- tabs, and carriage returns.
```

---

## Basics

![](./moduleimage.png) (just "./theimagefile.name", saved in the same directory)

Type: VCA / PB&J Sandwich / ABCDE (Don't worry if you don't get every last usage case)

Size: X HP (If you don't like squinting, use aP-Modules HP Meter :-D )

Modeled After/Inspired by: (If Antonio included references to hardware/software in the changelog, the module browser in Rack (like he did the Complex DAHD), or on a FB post, put those here! Same goes for requests from people for a module that does XYZ - Put their Name in here)

---

## Functions by Section

### Section A

(in reference to the image - see MetaAardvark for a great example)

Try and describe what the control -does-, what voltage range a CV Input accepts, the kind of signal an output generates, etc. Usage has it's own section, so please try and limit things to specific controls here.

FUNCTION NAMES should be in ALLCAPS.

If you need to add a specification in a text block, try to be as clear as possible, ie. "-666.00 V to +666.00 V ***(Default: 0.00 V)*** ". If you can't fit the phrase inline, separate it out like these:

***Default Clock Rate: 10.00 Hz***

***Min Clock Rate: 0.01 Hz***

***(Anything between 3 \*s will be in bold -and- italic)***

### Section B

If you need to write in point form:
- Dash space start typing for your first level items
  - space space dash space for your 2nd level
- Don't add extra lines between list items

Start writing again after

### Section C

### Section D

(As many sections as make sense. You're not required to use 4!)

---

## Usage

Describe how to -use- the module. 

---

## Sample Patches

\[typethefullpatchname.vcv] \(\./typethefullpatchname.vcv) 

- save the patch in the same folder. Please don't link to external services, as they're not owned by Microsoft (like Github), and who knows if/when they'll go down. 

If your patch isn't self-evident based on how you've described the module above, try and include some kind of basic write-up.

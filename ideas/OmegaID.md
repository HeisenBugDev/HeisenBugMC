# OmegaID

OmegaID is a new ID system for minecraft that will hopefully fix the ID conflict disaster! This idea file was made from the OmegaID.txt log that you can find in logs/OmegaID.txt

## The problem

ID conflicts suck. They just do. The problem is that with the current system there is nothing we can do that will last. **We can't replace ids with strings because that is >= 8 bits per character and that would result in MASSIVE file sizes** So what can we do?

## The solution

We keep ids (they are 1.5 bytes per id) and add a way for mods to use strings as the "ids" and then the game automatically translates it to an id on runtime. Here's how it will work:

You have a plain ol minecraft. You then create a world and along with that a custom file that has a list of names and corresponding ids. Here's the fun part. When you add in a mod, it gets the next ids in the list. So if you add in IC2 first it gets smaller ids. If you then installer BuildCraft then the ids will start after IC2 ids. If you install them in the opposite order the BC ids will be smaller.

_Each world can have different ids depending on what order you installed the mod and created the world_ This means that the server will have to give the client this file so that the client knows what ids to use for which blocks.

Now what if I remove a mod? If you load up a world and the names in the file are not real block names then it will only remove the ids from the list if you allow minecraft to load the world (the whole this world has block id blah but it doesn't exist).

So what if we have blank wholes of ids? We have two ways which we have not decided.

 - Shift all the ids down and do the same in the world (SLOW)
 - Leave the whole there and when new ids are added fill in the space (FASTER)

## Possible issues

 - World data gets loaded before id conversion file does.

## Possible solutions for the issues

 - Have client recieve all the data and just not allow it to do anything until the id conversion file is recieved
# BotW Alternative Content Structure

The modding community for *The Legend of Zelda: Breath of the Wild* encountered two problems. Firstly, mod creators were spending large amounts of time unpacking and repacking archives, and converting file formats. These tasks could be automated to save time. Secondly, mod users were encountering many mods containing files that were incompatible with each other. Many of these files could be merged to be made compatible, but this merging process required the skills and knowledge of a mod creator.

In order to attempt to solve both of these problems, this document defines an alternative structure for *BotW*'s ROM content files, intending to more closely resemble a set of source files. It defines the method to convert the content files to this alternative structure, and also how to convert back to the original structure. This structure is intended to be used in two ways:

 1. Mod creators will use a tool to convert *all* of the game's content files to the alternative structure. This will eliminate the need to unpack access them.
 2. Mods will be distributed containing a *subset* of the alternative structure (specifically, *only modifed files*), and mod users will use an installer tool to convert them back into the original structure (with data being taken from the user's game dump where necessary). This will reduce the file size of distributed mods, and allow the installer tool to easily merge mods which would ordinary conflict.

## Converting to the alternative structure

 1. Decompress all Yaz0-compressed files. 
 2. Unpack all SARC archives, and decompress all their Yaz0-compressed contents. If the archive extension is *pack*, *sbactorpack* or *sbeventpack*, unpack the contents into the root content directory. Otherwise, unpack into a directory with the same name (including the extension) and location as the original archive. If any file clashes occur, the clashing files are guaranteed to have the exact same contents.
 3. Convert all AAMP and BYML files to YAML, using the *yaml-aamp* and *yaml-byml* specifications respectively. They are to be named using the pattern "*filename.ext*" --> "*filename.ext.yml*".

## Converting back to the original structure

1. 
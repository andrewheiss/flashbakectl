# flashbakectl #

flashbakectl is a simple front end that loads and unloads plist daemons for OS X's `launchd`, allowing you to control when [Flashbake](http://github.com/commandline/flashbake/ "commandline's flashbake at master - GitHub") is automatically run. 

## Installation ##

Although OS X is built on Unix principles and has a working version of `cron`, Apple suggests using `launchd` to control scheduled events. `launchd` loads plist files to run system and user agents and daemons, giving you finer control over when scripts are run.

1. **Install [Flashbake](http://github.com/commandline/flashbake/ "commandline's flashbake at master - GitHub").** Configure it to work with a repository. See the documentation for Flashbake for details.

2. **Install flashbakectl.** Place the file `flashbakectl` in a folder somewhere in your path. To see or modify your path, edit `~.bash_profile`. On my computer I use store my executable scripts in `~/bin`, which is included in my path (`...some/directory:/Users/andrew/bin:$PATH`).

3. **Make flashbakectl executable.** Type `chmod +x flashbakectl`.

4. **Install [Lingon](http://sourceforge.net/projects/lingon/files/ "Browse Lingon Files on SourceForge.net").** A plist file is simply an XML file, as you can see from `sample.plist`, but I suggest using a graphical plist editor, like the open source [Lingon](http://sourceforge.net/projects/lingon/files/ "Browse Lingon Files on SourceForge.net") (which has sadly been abandoned by the author), to manage your custom plists.

5. **Create your plist file.** Create a new "My Agent" in Lingon. Name it something like `com.yourname.flashbakectl`. Type the full path to flashbakectl with the `-a` flag added (which will run the script). For example, `/Users/andrew/bin/thesis_flashbake -a`. Modify the scheduling options (you'll probably only want it to run every 15-20 minutes, not). See the included screenshot for a full example.

6. **Configure flashbakectl.** Update the variables `FLASHBAKE`, `PLIST`, and `PROJECT` to match your environment.

7. **Test everything**. Run `flashbakectl -m` to manually run Flashbake with all your configuration. If that works, run `flashbakectl -l` to load the plist.

## Regular use ##

Run `flashbakectl -l` before you begin writing to load the plist. Every 15 minutes (or whatever interval you set), `launchd` will automatically run `flashbakectl -a`, which runs Flashbake. When you are done writing for the day (or writing session or whatever), run `flashbakectl -u` to unload the list and essentially turn off the scheduled committing.

## License ##

flashbakectl is licensed under the MIT License:

Copyright (c) 2009 Andrew Heiss (http://www.andrewheiss.com)
 
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
 
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
 
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
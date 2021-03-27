Blackboard Scraper
========
## EDIT: The fork is now private

Why? Beacuse creating this sort of script could make me a target if other people decide to use my script to mass-download THEN mass-upload copyrighted material to another website.

Sorry, but personally I think my record is more important than how open source this project is, in this particular case.

I don't want any unecessary risk that I can avoid. I know that using the proper license can legally mean no warranties and I cant be held liable etc etc, but not worth the effort if it does happen and I have to defend myself. SO I'm making it private.

Remember that the original reason I made this was because I like having files on a real filesystem, not on some web application.

If you want clues on how I implemented this fork:
* Use selenium to automate microsoft SSO login
* add auto-unzip with rubyzip
* Modify some stuff with the path (add a metadata file to show original name/id) so I can shorten the lengths for my windows machine
* Add the ability to download the files from the _descriptions_ of folders (not inside the folders)
* Add a $WAIT to reduce stress on the server.

---

## Fork of https://github.com/JaciBrunning/BlackboardScraper
## Use at own risk!

### Why?
Becaues I prefer learning with the resources on a real filesystem (with the ability to copy/paste/etc.), rather than a web interface/app.

### Use

This tool allows you to quickly and easily dump all unit materials in Blackboard into a folder (`out`).

This tool downloads most unit materials, but will NOT download iLectures, announcements, grades or external links.

## Installation
- Download or clone this repository to somewhere on your system  
- Install Ruby
    - Mac: should already be installed. Optionally install with Homebrew (`brew install ruby`)
    - Linux (Debian/Ubuntu): `apt-get install ruby-full`  
    - Windows: https://rubyinstaller.org/  
- Install the `nokogiri` gem  
    - `gem install nokogiri` in a shell terminal (this will take a while)  
    - Edit: Installing this gem on msys (Windows) doesn't work. Need to use WSL or something else.
- Install the `rubyzip` gem (OPTIONAL - to automatically unzip any zip files downloaded)
    - `gem install rubyzip`
- Download `chromedriver.exe` to this directory. Get it from https://chromedriver.chromium.org/.
- Install python 3
- Install selenium for python with `pip install selenium`. We need this to automate the Microsoft SSO/login.

## Usage
- Run the `scraper.rb` file:  
    - `ruby scraper.rb` - It will ask for your Blackboard username (student ID) and password, and will then work on its own, downloading course materials. It will take quite a while, and it's recommended to do it on a fast internet connection.  
- Your course materials will now be in `out/`  
- The script has a wait timer. Modify `$WAIT = 5` in `scraper.rb` to whatever seconds you want to wait between operations. This is to reduce stress on the server.

## NOTE!
For units that like to have long folder/file names, you may find PDF readers or other applications fail to open the files and will promptly crash with no explanation. This is because the full path of the downloaded asset is longer than the system max filepath length (260 characters on windows, 1016 characters on macOS, 4096 on most linux distros). 

Fix: move the file somewhere with a shorter path (like your Desktop, or Documents), or rename the files/folders after they have been downloaded to something less long.

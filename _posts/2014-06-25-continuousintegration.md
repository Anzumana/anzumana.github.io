#Xcode Server + Github Continuous Integration
First of all this [blog post on xcode server](http://ikennd.ac/blog/2013/10/xcode-bots-common-problems-and-workarounds/) helps a lot.

I followed the tutorial that apple offers inside of the **OS X Server** Application. 
Since i use ssh for authentication for my private github repositories i needed *upload my public key to github*. 
That for some reason didn't work so i generated a new ssh key inside of the OS X Server Application.
And uploaded that new public key. 
Then it worked but xcode gave me an error for the readme.md file.
Removing it and adding it again through the Xcode UI fixed that.
Then everything worked. :) 
Happy Coding.


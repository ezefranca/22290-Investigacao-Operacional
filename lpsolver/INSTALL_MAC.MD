<html>
<body>
<h1>Steps to install and run lpsolve on a Mac</h1>
<p>
There are several ways to install lpsolve on a Mac.  Here is one way.
</p>

<ol>
<li>Go to <a href="https://sourceforge.net/projects/lpsolve/">the Sourceforge page for lpsolve</a>.
</li>
<li>Click the big green Download button and, when prompted, save the downloaded file to your Downloads folder.
	<p style="font-weight:normal;">This will download the latest source code for lpsolve
	to your machine.  It does not take long: lpsolve is a small program.
	The file will have a name like <b>lp_solve_5.5.2.11_source.tar.gz</b>.
	(The 5.5.2.11 is a version; you might get a new version.)
</p>
</li>
<li>In Finder, navigate to your Downloads folder and double-click on the downloaded file.
	<p style="font-weight:normal;">This will decompress the file and expand it into a set of folders.
	You should then see a folder named something like <b>lp_solve_5.5</b> in your Downloads folder,
together with the downloaded .gz file.</p>
<li>Open the application Terminal on your machine.
	<p style="font-weight:normal;">You may find it in the Utilities folder
	inside your applications folder.</p>
</li>
<li>In Terminal, navigate to your Downloads folder.  To do this, in the Terminal window,
	type the following commands, each followed by the enter key:
<pre>
cd
cd Downloads
cd lp_solve_5.5
cd lp_solve
sh ccc.osx
</li>
</pre>
This last command runs the shell script <b>ccc.osx</b> to set
	up lpsolve.  You may see some warnings; you can probably ignore them.

<div style="border: 2px black; border-style:solid; padding: 5px; margin: 5px;">
However, if you see an error like "xcrun: error: invalid active developer path",
this most likely indicates that the lpsolve install script is looking for xcode command-line
tools on your machine and cannot find them.  In this case, try adding the xcode tools with this command:
<pre>xcode-select --install</pre>
 It will take a few moments to this do installation.  Then open a new terminal window, and try step #5 above again.
 </div>

	These commands will create a sub-folder, <b>bin</b>
	containing the executable lp_solve (it may be in a further sub-folder, named something like
	<b>osx64</b>.)
</li>
<li>Navigate to the subfolder containing lp_solve by executing these commands in Terminal:
<pre>
cd bin
cd osx64
ls
</pre>
	<p style="font-weight:normal">This last command, ls, will <i>list</i> the files
		in this folder: you should see <b>lp_solve</b> listed.  This is the
		executable application.
</p>
</li>
<li>To test lpsolve and see that you've installed it, you will need a test lp file.
	You can use <a href="test.lp">test.lp</a>.  Use Finder to put this file in the same
	folder with lp_solve.
</li>
<li>In Terminal, run lp_solve on this file with the command
<pre>
./lp_solve test.lp
</pre>
lpsolve will run and give you the following result:
<pre>
Value of objective function: 4.61764706

Actual values of the variables:
x                         3.58824
y                         1.02941
</pre>
<p style="font-weight: normal">This indicates that these values of x and y, the
	minimum sum x+y, 4.61764706, is achieved with x=3.58824 and y=1.02941 (approximately)
	while satisfying the specified constraints.
</p>
</li>
<li>Congratulations! You have succesfully installed lpsolve!
</li>
</ol>
<h2>Additional notes</h2>
<ul>
<li style="font-weight:normal;">After the above installation lp_solve now lives in
	that one location deep down in your Downloads folder.  You can move lp_solve
	anywhere you want to, so you might want to move it somewhere else (I periodically
	delete everything in my Downloads folder so it's not a good permanent home for
	anything.  I recommend moving it somewhere else, somewhere safe.
	Let's say that you put it in a folder called <b>lpsolve</b> that you create in your <b>Applications</b> folder.
	Then what you can do is create an alias so that, in Terminal, you can run lp_solve from any location.
    </p>
    <p>
  To create an alias, you will need to edit your bash profile.
	In your home directory, there may be a file like <b>.bash_profile</b> (if it is not there, you can create it).
    Note that this
	is a "hidden" file (since it starts with a dot), so you may not see it in Finder.
	You will need to make hidden files visible; depending on your OS version, there are
	various ways to do this.  In Terminal, the command
    <pre>ls -a</pre>
    will list all files in the current directory, including hidden ones.
    If you don't see <b>.bash_profile</b>, you can create one.

	Either edit <b>.bash_profile</b> and add this line:
	<pre>
alias lp_solve='/Applications/lpsolve/lp_solve'
</pre>
or create a new file, <b>.bash_profile</b>, containing that line.
</p>
<p>
	Save the file, then restart Terminal and you will be able to execute lp_solve from any folder
	(which will be useful since you will likely create multiple folder for the different
	LPs we'll be looking at in the course.) The command to execture lp_solve will look like
<pre>
lp_solve test.lp
</pre>
where test.lp is the text file containing the LP you want to solve.
	Note that the "./" is not needed if you make the alias (the ./ indicates to the operating
	system that you want to run the application lp_solve that is right there in the current
	directory.   With the alias, the operating system is told where to find the application.)
	<br>
	<br>
	Alternatively, in Terminal, the command
<pre>
echo 'alias lp_solve="/Applications/lpsolve/lp_solve"' >> .bash-profile
</pre>
will add the alias to <b>.bash_profile</b> without using an editor (or create it if the file does not already exist).
This also will not require you to make hidden files visible in Finder.
</li>

</ul>


<!--
<h1>Latest OSX version</h1>
<p style="font-size: 20px; font-weight:bold; color:#ff0000;">
	Homebrew appears to not be working with lpsolve.  Please use the instructions
	further down the page ("Older OSX version").
</p>
<div style="background-color:#777777";>

<p>
If you are running the latest OS, you should install lpsolve using
<a href="https://brew.sh/">HomeBrew</a>, which is a very useful tool in itself.
Once you have installed Homebrew, you can install lpsolve with the commands
</p>
<pre>
brew tap brewsci/science
brew install lp_solve
</pre>

executed one at a time on the command line in Terminal.
</p>
<p>Then follow these steps to run lpsolve.</p>
<ol>
<li>Get or make an LP file.</li>
<p>
We need an LP to feed to lpsolve.
</p>
<p>I strongly recommend getting a dedicated text-editor.
You can read about many free ones <a href="https://en.wikipedia.org/wiki/Category:Free_text_editors">here</a>.
I use <a href="https://en.wikipedia.org/wiki/BBEdit">BBedit</a>,
which is free, though it occasionally asks you to "upgrade", which costs money.
I've been using it for free to 20 years or more.  There are many totally free, open source editors you could use.
</p>
<p>In a text editor, create an LP in lpsolve format.  Here is what that might look like (I just made up this LP):
<pre>
min: x+y;
3*x+5*y>=12;
7*x+y>=15;
</pre>
<p>
Save this somewhere, like your Desktop.  I saved it as <i>test.lp</i>.
I use the .lp suffix just to remind me that it is a file for lpsolve; you could use the more generic .txt.
</p>
<li>Run lpsolve on your LP</li>
To do this, change directory (cd) to where you save test.lp, and then execute the command:
<pre>lp_solve test.lp</pre>
</p>
<p>
The result will look like this:
</p>
<img src="img/lpsolveLatestOSX.png">
<p>This shows us that lpsolve solved the LP, and printed out the solution, both the
value of the objective function and the value of x and y at the solution.</p>

</ol>

</div>


<h1>Older OSX version</h1>

<p>
If you have an older OSX or you do not want to install Homebrew, try these steps.
<p>

<ol>
<li>Download lpsolve.</li>
<p>If you click on the big green "Download" button
<a href="https://sourceforge.net/projects/lpsolve/">on this page</a>,
you will download lpsolve.
<img src="img/sourceForge.png">

The download will take very little time: it is a small program.
</p>

<li>Go to your Downloads folder and uncompress/unarchive lpsolve.</li>
<p>
You should see a file with a name like
<pre>lp_solve_5.5.2.5_exe_osx32.tar.gz</pre>
If you double-click on this, you will uncompress and unarchive it, and you
should see a folder named
something like <pre>lp_solve_5.5.2.5_exe_osx32</pre>
The folder may already be there, so you don't need to double-click on the gz file.
</p>

<li>Open Terminal</li>
<p>Terminal is an application.  You can find it in the Utilities sub-folder of
your Applications folder.  You will get a "terminal window", like this
(your colors and text may be different):
<img src="img/terminal1.png">
</p>

<li>Navigate to the lpsolve folder in your Downloads folder.</li>
<p>
You need to use the linux command cd to "change directory" to the
lpsolve folder.  When you start Terminal, you start in the directory
(directory and folder mean the same thing)
above your Downloads folder, so you need to "cd" to you Downloads
folder, then "cd" to you lpsolve folder.  Here's what that looks like
in Terminal:
<img src="img/terminal2.png"><br>

At this point, if you execute the "ls" command, you will see a
<i>list</i> of the contents of the current folder:<br>

<img src="img/terminal3.png">

<br>
Notice that these are the same files that you see if you open this folder in Finder.
</p>

<li>Get or make an LP file.</li>
<p>
We need an LP to feed to lpsolve.
</p>
<p>I strongly recommend getting a dedicated text-editor.
You can read about many free ones <a href="https://en.wikipedia.org/wiki/Category:Free_text_editors">here</a>.
I use <a href="https://en.wikipedia.org/wiki/BBEdit">BBedit</a>,
which is free, though it occasionally asks you to "upgrade", which costs money.
I've been using it for free to 20 years or more.  There are many totally free, open source editors you could use.
</p>
<p>In a text editor, create an LP in lpsolve format.  Here is what that might look like (I just made up this LP):
<pre>
min: x+y;
3*x+5*y>=12;
7*x+y>=15;
</pre>
<p>
Save this in the directory with lpsolve.  I saved it as <i>test.lp</i>.
I use the .lp suffix just to remind me that it is a file for lpsolve; you could use the more generic .txt.
</p>
<li>Run lpsolve on your LP</li>
To do this, execute the command:
<pre>./lp_solve test.lp</pre>
</p>
<p>
The result will look like this:
</p>
<img src="img/terminal4.png">
<p>This shows us that lpsolve solved the LP, and printed out the solution, both the
value of the objective function and the value of x and y at the solution.</p>
-->
</body>
</html>

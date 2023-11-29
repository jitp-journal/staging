# Instructions for Stagers

Welcome, everyone! The steps below go into some detail, but the processes they describe are actually pretty simple once you're up and running. From a styled Word document, you can have working HTML ready for Manifold in just seconds.

Most of the complexity here, then, is (a) getting set up and (b) making sure it worked.

1. Styling the document in Word or OpenOffice
2. Running the Mammoth script
3. Compress the resulting directory
4. Test in Manifold
5. Make changes if necessary
6. Deploy in Manifold


## 1. Styling the document in Word or OpenOffice

Stagers can now use built-in Styles features in your favorite word processors to mark paragraphs (or character spans) as the specific content types we use at JITP, from headings to abstracts to figures and more. Additional guidance coming soon (though some of it is included in the files themselves), but here are the relevant files:

* [MS Word style template](jitp-staging-test.dotx)
* [OpenOffice style template](jitp-staging-test.odt)

Be sure to save your file as .docx, whichever software you're using.

## 2. Running the Mammoth script

Mammoth is a library for transforming .docx files into .html files. You'll need Python to run our custom JITP Mammoth script, but once you're set up, it's just one line at the [command prompt](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Understanding_client-side_tools/Command_line) (a.k.a. Terminal) and you're basically set!

<details><summary>2a. <strong>Set up your environment</strong>. Some things you only have to do the first time you stage; after that, you can go straight to 2b.</summary>

<ul>
<li>If you haven't yet, <a href="https://www.python.org/downloads/release/python-3120/">install Python 3</a>.</li>
<li>With Python installed, run <code>pip3 install mammoth</code> to make sure you have the library on your system.</li>
<li>Download the JITP conversion script: <a href="to-html.py">to-html.py</a>. For convenience, we recommend that you place this in the directory where you'll keep your .docx files to convert. For the sake of these instructions, let's call that directory <code>staging</code> and suppose it's a subdirectory of <code>jitp</code>. If you use some other location, make the appropriate substitutions as we move forward.</li>
<li>Find your files. At the command line, navigate to the staging directory with the <code>cd</code> command (e.g. <code>cd ~/jitp/staging</code>).</li>
<li>Change the JITP script's mode to executable. From within the staging directory, tell your computer that the file contains commands by typing <code>chmod +x to-html.py</code>.</li>
</ul>

<p>Again, <strong>you should only have to do these steps once</strong>, when you first start using this process. For all subsequent times, you can skip straight to the steps below.</p>
</details>
<br/>

2b. **Run the script**. In your command line, navigate to the staging directory (e.g. `cd ~/jitp/staging`). If the file you're converting is called `myfile.docx`, and both that file and the conversion script are in that directory, then the command to run is `python3 to-html.py myfile.docx myfile`.

<details><summary>More detail on what each piece of that command does, so you can modify if necessary</summary>
<dl>
<dt><code>python3</code></dt>
<dd>This instructs the computer to use Python 3, even if you have Python 2 on your computer. This is essential for making sure the program can find the mammoth library.</dd><br/>
<dt><code>to-html.py</code></dt>
<dd>The path to the conversion script. If you're in the same directory, you don't need a prefix. If you keep the file somewhere else, just add the relative path to the file's location, e.g. <code>../staging/to-html.py</code>. Note that the two dots mean "go up one directory."</dd><br/>
<dt><code>myfile.docx</code></dt>
<dd>The path to the file you're converting. If your filename has spaces, you can escape them with a backslash, like this: <code>my\ filename\ with\ spaces.docx</code>. You can probably get the command line to autocomplete the filename by typing in the first few letters and hitting <code>tab</code>.</dd><br/>
<dt><code>myfile</code></dt>
<dd>The name of the output directory. Avoid spaces in this directory name. Often using the first author's last name is a good approach. And if you stick to all lowercase letters, you never need to remember whether the filename is capitalized.</dd><br/>
</dl>
</details>
<br/>

And that's it! If the setup in 2a was successful, you should see the new output directory appear in your file system as a subfolder of `staging` (or whatever your current directory is called). The output directory will contain one .html file and a separate image file for each image in the original document.

## 3. Compress the resulting directory

Using your favorite software<sup>*</sup>, compress the output directory from step 2 into a .zip file.

<sup>*</sup> Your operating system may come with compression pre-installed. Try right-clicking the directory name and look for a "compress" option in the contextual menu.

NB: this new .zip file should live *alongside* the folder it came from, *not* inside it. (Otherwise, your folder will contain a copy of itself.)

## 4. Test in Manifold

You're now ready to upload the .zip file to Manifold! We'll make sure everything looks okay here before sending the file back to the Managing Editor.

4a. **Open a test project**. Unless you have direct admin access to the issue at hand (which has to date been given only to the Managing Editor and Issue Editors), you'll want to create a Project just for visually confirming that the files look right. Once you've done this, though, you can keep using it for future issues as well.

4b. **Add the text**. Within the admin view of that test project, click the "Add a new text" button. In the sidebar that appears, select the .zip file from step 3 and Continue. Start Ingestion and click the button to acknowledge when the process is Complete.

4c. **Open the text's backend**. The filename in Manifold should be the *title* of the file you uploaded (rather than the author name). Click on it from the admin view to get a new menu of options, including Styles.

4d. **Add JITP styles**. Click on the Styles option, then "Add a New Stylesheet." In the Name field, write JITP. In the Source Styles box, paste in the contents of the JITP CSS file. (As of Issue 22, that was [JITPv2.css](JITPv2.css).) This is what will make the abstract, blockquotes, bibliography, figure captions, etc look like our journal wants them to look! To complete the process, under "Apply to these text sections" click "Add all" and then "Save Stylesheet".

4e. **Remove non-JITP styles**. Back on the Styles page, you should now see JITP added to the list next to something called _Global Styles_. We want to get rid of the latter, so click on the Trash icon next to Global Styles and confirm that Yes, you want to delete this stylesheet. (Don't worry: it'll appear on its own for the next file you upload).

4f. **View the file**. Finally, you can click the View button just below the article title. You should see the article appear as it will on the official JITP site. Skim through and note anything missing or messed-up – though we hope you won't find any!

## 5. Make changes if necessary

If something is *systematically* wrong, we should probably fix the script. Check the [issue queue](issues) to see if someone's already logged the bug, and if not, create a new one.

If anything looks *individually* off, you'll need to go back to the relevant file, make the change, and repeat the process above.

* If you feel comfortable doing so, you can make changes directly in the html file – though be sure to use a plain-text editor like Pulsar or Visual Studio Code rather than a word processor.

* If you have to change image files (e.g. to get better resolution), you can just replace the old files with new ones. As long as they keep the same name, you won't need to change the html.

* If you have to go back to the Word document and change the styles as in step 1 above, you'll need re-run the mammoth script again as in step 2. However, the script will probably complain that the destination folder already exists. In that case, delete that output folder and try again.

When you're done making changes and want to confirm that they worked, compress the folder again as in step 3 above, then head back to Manifold. You can use the "Reingest" menu item on that specific text's admin view to avoid creating multiple copies of the same article.


## 6. Deploy in Manifold

And with that, your part is done! Send the final successful .zip file back to the Managing Editor by whatever means you received it. (E.g. through a shared folder in Google Drive.) The M.E. or the Issue Editors will take it from there.

And thanks!
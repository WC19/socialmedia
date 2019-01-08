## Welcome
The Social Media Ostracism paradigm is a web-based experimental manipulation of ostracism and social exclusion, designed for research purposes. 

![preview](https://dl.dropboxusercontent.com/u/8615956/Capture.PNG)

On this page you can find:

- Preview of the paradigm (online version)
- How to use the online version of the paradigm for experimental purposes
- How to download & customize the study 
- How to install and run the downloaded versions on a personal computer
- Suggestions on how to run the customized study online

### Try it out
To try out the Social Media Ostracism paradigm follow one of these links:
- [Try out exclusion condition](http://smpo.github.io/preview/index.html?c=1&p=999)
- [Try out inclusion condition](http://smpo.github.io/preview/index.html?c=2&p=999)

### More about the paradigm
Social media ostracism is a type of social exclusion which happens via social media websites, such as Facebook, Twitter, blogging platforms, or forums. In the paradigm, feelings of exclusion are conveyed through the number of "likes" that people receive on their personal profiles during a group intro task. A detailed description of the procedure and report of the manipulation effects can be found in [this manuscript](https://dl.dropboxusercontent.com/u/8615956/ALevordashka_SocialMediaOstracism.pdf).

We recommend that you end the paradigm with an online survey, which contains manipulation checks, dependent measures, and/or connection to subsequent tasks. If the entire study is conducted online and with no interruptions, the participants will be more likely to think that they are interacting with other participants (rather than computer scripts). 

The Social Media Ostracism paradigm was inspired by Cyberball - a virtual ball-tossing game. You can find out more about Cyberball and research on ostracism on https://cyberball.wikispaces.com/


### Use it in an experiment
To use the paradigm in your own experiment without additional customization of instructions, or timing, you will only need to modify the following link:

```markdown
http://smpo.github.io/preview/index.html?c=XX&p=YY&redirect=ZZ
```

| Substitute...       | with...   |
| ------------- |:-------------:|
| `XX`             | `1` for ostracism condition, `2` for inclusion, `3` for overinclusion |
| `YY`             | unique participant number |
| `ZZ`             | Encoded survey link |

> To encode your survey link, open http://smpo.github.io/dencoder/ paste the link to your survey in the textbox, and press "Encode." Use the encoded survey link as part of the URL in place of `ZZ`. 

If you wanted to set up the study for participant number 5, who should be in the inclusion condition, and you want to redirect the participant to a Qualtrics questionaire available under the address [http://fppvu.qualtrics.com/SE/?SID=SV_a9u9MdnpIRuxctT](http://fppvu.qualtrics.com/SE/?SID=SV_a9u9MdnpIRuxctT), the link to the study should be as follows:

```markdown
http://smpo.github.io/preview/index.html?c=2&p=5&redirect=http%3A%2F%2Ffppvu.qualtrics.com%2FSE%2F%3FSID%3DSV_a9u9MdnpIRuxctT
```

After the paradigm is finished, the participant will be redirected to the survey link as specified by the parameter `ZZ`. Any survey link can be specified. The script will extend the survey link by additional variables that can be read out by the survey, mainly to pass on the condition, participant number. In addition, also information about the chosen avatar, the username and description provided by the participant are transmitted, these may be analysed in order to identify participants who did not take the paradigm seriously (e.g. nonsense description provided). 

In our example, the participant could be redirected to the following URL after the paradigm is finished:

```markdown
http://fppvu.qualtrics.com/SE/?SID=SV_a9u9MdnpIRuxctT&c=2p=5&av=23&u=JohnDoe&d=ABC
```

Which would mean that the sample participant number 5, who was in condition 2, chose JohnDoe as a username, picked avatar 23, and described himself with the text ABC.

[Here you can download a sample Qualtrics questionaire](http://smpo.github.io/Social_Media_Ostracism_MCDV.zip), that reads out the transmitted variables, and provides a number of follow-up questions as manipulation check. [More information about how to import a questionaire into Qualtrics](http://www.qualtrics.com/university/researchsuite/advanced-building/advanced-options-drop-down/import-and-export-surveys/).


### Set it up on your own computer or server
For more customization, such as modified task instructions, or different timing of the paradigm, you can download the source code of the paradigm.
[Download the code as a ZIP](https://github.com/smpo/socialmedia/zipball/master) (or [TAR](https://github.com/smpo/socialmedia/tarball/master)) file and extract the files to your computer. To run the study, open the file `index.html` in an internet browser. By default, an internet connection will still be necessary as not all Javascript libraries are included in the ZIP file. 

By customizing the code, you can easily make changes to the following parameters: 
* The task instructions
* Avatar pool from which the participant can choose their own avatar
* Number of people the participant "interacts" with
* Profiles (avatars + descriptions) of other group members
* Number of "likes" received by the participant and other group members
* Change the word "like" to another word or symbol

##### To adjust various settings:

1. Open the file `main.js` (from the folder on your computer) in a source code editor (e.g. [Notepad++](http://notepad-plus-plus.org/)) 
2. In the beginning of the code, variables for settings are defined, including the length of the task, and the number of likes participants reveice in each condition. Comments explaining the variables are provided in the code.
4 Change variables in the `main.js` file on your computer (using the editor), according to the instructions document
5. Save the changes made to the `main.js` document

[Click here for an annotated version of main.js](http://smpo.github.io/annotated-mainjs/), as an quick online reference.

##### To change the study instructions:
 
Similarly, to edit task instructions, open the file `index.html` on your computer with an edtitor. Edit the task instructions according to the instructions provided within the document, and save your changes.

[Click here for an annotated version of index.html](http://smpo.github.io/annotated-indexhtml/), as an quick online reference.

##### To change the group member profiles (descriptions and avatars):

To change the group member profiles (descriptions and avatars) open the file `profiles.json` in an editor, and adjust the contents to your needs. 

The following scheme describes a group member, his avatar, description and the likes he receives.

```json
{
        "username": "Georgeee",
        "avatar": "avatars/others/george.png",
        "text": "I'm a 19 year old dude from Wisconsin (commence making fun of my accent). I love music and lately you can catch me listening to nothing but Joy Division, Echo & the bunnymen, and the smiths. Besides music I like learning languages, psychology, drawing, and writing.",
        "likes": [45000, 50000, 110000, 150000]
}
```

According to this code, the group member will be called Georgeee, and he will have an avatar image with the filename george.png placed in the folder avatars, subfolder others. Georgeee will reveive 4 likes overall for his description, at 45s (45000ms), 50s, 110s and 150s.

Note that the personal description needs to be entered without line breaks, as it appears in the default descriptions. To change the number of "likes" in each condition, add or remove timepoints. Make sure that every timepoint is preceded by a single comma. The likes entry should not be empty or left out. If you want to create a member that does not receive any likes, simply change the timepoints to high values (longer than the time of the task).

The avatars used in the previews are not meant for redistribution and thus not included in the version for download. You will thus need to create your own avatars. Avatars in the previews were created using a [free avatar generator available online](http://pickaface.net/). All avatars have to be 250x250px, placed in the subfolder "others" (located inside the folder "avatars" in the main study folder you extracted on your computer or server). Note that the names of the image files must exactly match the names in the source code (including whether the file extension is upper or lower case). 


##### Running the study from your own server:

The task can be easily made available online, as it runs in a browser and has minimal server requirements. Any server that allows hosting of static webpages should work, and offers at least 5 MB of disk space should do, meaning that it can potentially be hosted for free. The files from the computer are transferred to the remote server for example by means of a FTP program. 


## Question and Issues

You can [submit a new question question or issue](https://github.com/smpo/socialmedia/issues/new) using GitHub.


## Citation

[tba]
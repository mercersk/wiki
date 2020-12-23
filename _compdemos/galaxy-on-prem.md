---
title: Galaxy Service on Gizmo (beta)
last_modified_at: 2020-06-16
main_author: Dirk Petersen
primary_reviewers: atombaby, k8hertweck
---

Galaxy is an open, web-based platform for accessible, reproducible, and transparent computational research, particularly for genomics data. 
Other organizations make [Galaxy](https://usegalaxy.org/) available for free use by academic researchers,
but this requires you to transfer your data,
and the computational capacity is limited since it is shared with many other people.
Our current method of supporting Galaxy for the Fred Hutch research community is via our on-premise compute clusters, 
`rhino` and `gizmo`.
Individual researchers have the ability to create, administer, and run their own instances (copies) of the Galaxy platform, 
including choosing and loading all software necessary for their analysis. 

The steps to run Galaxy include:
- create your Galaxy instance
- load your data and software
- develop and implement your workflow

## Creating your first Galaxy instance

The steps to create a Galaxy instance include:
- logging on to `rhino`
- running the `galaxy` command (takes ~30 minutes to create an instance)
- launching the Galaxy instance through a web interface

While this does require a bit of setup when getting started,
you only need to do this once,
after which you're able to retrieve the same instance and begin working with data more quickly.

Creating and using Galaxy on `gizmo` requires you to first log on to the Fred Hutch on-premise compute cluster `rhino`.
If you aren't familiar with this process, 
please see [this tutorial](/compdemos/first_rhino/).
Note that you will need to keep the shell window connecting you to `rhino` open while the instance is being created.
One way to ensure this connectivity is to use [tmux or NoMachine](/scicomputing/access_methods/)] to ensure a long-running shell.

Once logged on to `rhino`,
run the `galaxy` command as shown below. 
To create your first instance,
type `1` and hit "Enter".
When prompted, type the name and hit "Enter".
This will create a new folder in your `/fast/` drive named `galaxies`, 
then download and install the relevant software in a folder within `galaxies` with the name you indicated.  

```bash
username@rhino03:~ galaxy
Enter number to select your Galaxy install
1) New-Install
#? 1 
New Install: Enter a name for the Galaxy instance: test_galaxy
```

FIXME: link to `sbatch`, discuss when window needs to stay open

A few minutes after the installation has been started you should receive an email like this:

![]({{ site.baseurl }}/compdemos/assets/2020-06-17-01-10-04.png)

Now you wait about 30 min. Then you should see the Galaxy login screen. Use your HutchnetID and password to login to the Galaxy interface:

![Login Screen]({{ site.baseurl }}/compdemos/assets/2020-06-17-01-19-43.png)


To terminate the Galaxy instance just type Ctrl+c twice inside the terminal Window. It will cancel the cluster job that runs Galaxy. 

## Rerunning a previously created Galaxy instance

```bash
username@rhino03:~ galaxy
Enter number to select your Galaxy install
1) /fh/fast/_HDC/user/username/galaxies/demo/
2) New-Install
#? 1
```
Select the options in the following menu that match
your intended use for the Galaxy instance.

## Accessing data

FIXME: note about data being copied to /fh/fast/

### From your own computer 

- "Get Data" in lefthand sidebar
- "Upload File from your computer" subheading
- "Choose local file" to navigate to location on your computer
- When all files desired are shown in the box,
click "Start" to begin the upload.

You'll see the upload box show a status update,
but this represents the status of the query being accepted. 
After closing that window,
you'll see your files represented in boxes on the righthand sidebar of your Galaxy interface.
When the box representing the data file changes from orange to green,
your data has completed uploading.

### From a URL

Follow the instructions above to load data [from your own computer](#from-your-own-computer),
but instead of "Choose local file,"
Select "Paste/Fetch data."
Paste in the URL where the data is located,
and proceed to Start the download job.

### Manipulating data in Galaxy

Under development: previewing, converting, and annotating data

## Installing software

- click on "Admin" in the top toolbar
- select "Tool Management" in the lefthand sidebar
- select "Install and Uninstall" in the menu below 
- search for the title of your software in the window that appears
- click on the software title in the search results
- click Install for the most recent version
- keep your tools organized by selecting an existing section,
or creating a new section under which your tool will appear

Click "Analyze data" in the top toolbar to move back to your original Galaxy view.
Watch the lefthand sidebar for the appearance of your software
(it may take a few minutes to install!).

## Suggestions for making the most of Galaxy

Please check the [Galaxy Documentation](https://docs.galaxyproject.org/) for more general information about using Galaxy. 

### Reproducible workflows

Under development

### Sharing your Galaxy work with Hutch collaborators

Under development

### Moving analyses to the command line

Under development

## Troubleshooting

### Proxy error

If you click on the link before your Galaxy instance has finished installing you will see a proxy error: 

![Proxy Error]({{ site.baseurl }}/compdemos/assets/2020-06-17-01-12-09.png)


Try again after a while. Then you should see the Galaxy login screen. 

### Wrong session token

When using Chrome, you might see this error message:

"Wrong session Token found." 

![Error with Chrome]({{ site.baseurl }}/compdemos/assets/2020-06-17-01-03-11.png)

To fix the issue please reset all fhcrc.org Cookies from your Chrome browser or use a new incognito window or use a different browser such as Firefox.

To remove Cookies from Chrome, go to:  
- Settings -> Privacy and Security 
- Cookies and other site data
- See all cookies and site data 
- in the upper right search for fhcrc.org
- click "Remove all shown" and restart Chrome

## Why this method of supporting Galaxy?

In the past,
fredhutch.io supported a Galaxy instance for our research community, 
and we tested using an external company, Globus Genomics,
to support Galaxy.

free use by academic researchers,
but this requires you to transfer your data,
and the computational capacity is limited since it is shared with many other people.

Other organizations make [Galaxy](https://usegalaxy.org/) available for free use by academic researchers,
but this requires you to transfer your data,
and the computational capacity is limited since it is shared with many other people.

- HutchNet ID authentication will be used 
- The instance will run with the launching user's permissions, these will be used for all data library access (e.g. file system)
- User maintains their own workflows (and thus can migratee them to newer installation of Galaxy if/when needed)
- User can self install the software as well as restart existing Galaxy servers, or make new ones if needed
- A simple database is provided (sqlite instead of Postgres)
- Each user can have access to multiple Galaxy instances (e.g. in case software updates need to be implemented)
- Galaxy server will run on a `gizmo` node, thus compute capacity is limited to single node (36 cores)

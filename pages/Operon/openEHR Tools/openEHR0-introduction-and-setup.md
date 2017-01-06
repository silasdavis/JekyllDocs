---
title:  "Introduction and setup"
sidebar: operon_sidebar
permalink: openEHR0-introduction-and-setup.html
summary: This section provides an introduction to the openEHR toolset and some initial setup instructions. The tools themselves are further explained in the subsequent pages in the openEHR Tools section.
---
These instructions will guide you through the process of setting up your computer with a set of openEHR clinical models (archetypes and templates), and a number of tools that will let you create new models or modify existing models.

## Non-Windows systems
Please note that the current Archetype Editor and Template Designer will only work with Windows, but it is not critical that every course participant has access to the tools during the workshop. It is generally beneficial for participants to work in small groups, and there are usually a sufficient number of Windows machines available.

For interest, a new set of open-source web-based tools is in early development and can be found at these links.<br />
[Archetype Designer](http://ehrscape.marand.si/designer/)<br />
[Template Designer](http://ehrscape.marand.si/designer/)<br />
[Source Code](https://github.com/openEHR/adl-designer)<br />

Please note that these tools are not yet suitable for training use.

## Install XMIND
As clinical modellers we make extensive use of mind map tools and find that the free XMIND tool is one of the best. It works on Windows, Linux and MacOSX.

<img src="\images\xmind_logo2.png">

You should download XMIND from [XMIND installer](http://xmind.net/downloads/).

## Setup Folder Structure
This is the folder structure you are going to create in this step:

```
openehr_training
 local
  archetypes
  templates
 remote
  ckm
   archetypes
```
&nbsp;

* Create a new folder in a location of your choice called ***openehr_training***.  e.g. ***..\Documents\openehr_training***

* Add a new folder named ***local*** under ***openehr_training***. e.g.  ***..\Documents\openehr_training\local*** .
	This will hold archetypes and templates that we create ourselves.

	* Add a new folder named ***archetypes*** under ***local***. e.g.  ***..\Documents\openehr_training\local\archetypes***
	* Add a new folder named ***templates*** under ***local***. e.g.  ***..\Documents\openehr_training\local\templates***

&nbsp;

* Add a new folder named ***remote*** under ***openehr_training***. e.g.  ***..\Documents\openehr_training\remote***. This will hold archetypes and templates that we download from other places.

	* Add a new folder named ***ckm*** under ***remote***. e.g.  ***..\Documents\openehr_training\remote\ckm***
	* Add a new folder named ***archetypes*** under ***ckm***. e.g. ***..\Documents\openehr_training\remote\ckm\archetypes***

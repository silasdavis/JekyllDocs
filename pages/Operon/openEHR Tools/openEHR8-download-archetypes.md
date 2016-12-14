---
title:  "Download Archetypes"
permalink: openEHR8-download-archetypes.html
---


The openEHR Foundation Clinical Knowledge Manager (CKM) is a web-based tool that stores openEHR clinical models that are developed collaboratively by the openEHR community and made freely available for others to use and copy.

Go to [openEHR Foundation CKM](http://openehr.org/ckm) then from the top menu select ***Archetypes->Bulk Export***.

<img src="\images\ckm_export.png" alt="CKM Bulk Export">

This will create a zip file with the latest versions of openEHR Foundation CKM archetypes.

Download this zip file and unzip it into the remote/ckm folder you created earlier e.g. ***..\Documents\openehr_training\models\remote\ckm\archetypes*** making sure you preserve the folders.

You should now have something like

```
* openehr_training
	* local
		* archetypes
		* templates
	* remote
		* ckm
			* archetypes
				* cluster
				* composition
				* demographic
				* entry
				* section
				* readme.txt
```

Depending on how your zip program works you may need to move the unzipped folders around to match this pattern.

### **CKM ‘GitHub mirror’**

Git is a common software version control tool. The CKM archetypes and templates are ‘mirrored’ out to a Git repository hosted at the [openEHR Github](https://github.com/openEHR/CKM-mirror).
<img src="\images\octocat.png" alt="GitHub">

If you are familiar with using Git, you can clone the repository as  ``git clone https://github.com/openEHR/CKM-mirror.git``.

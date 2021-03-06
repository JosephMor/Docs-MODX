---
title: "Securing a Media Source"
_old_id: "487"
_old_uri: "2.x/administering-your-site/media-sources/securing-a-media-source"
---

This article describes how to secure a Media Source to certain User Groups. It is recommended to read the [Adding a Media Source](building-sites/media-sources/creating "Adding a Media Source") article before reading this one. Before getting started, create a "Content Editors" user group, if you don't already have one.

Those installing new installs of MODX 2.2.0-pl will need to add the string "sources.modAccessMediaSource" (no quotes) to the comma-separated list of values in the "principal\_targets" System Setting. This is due to [this bug here](http://bugs.modx.com/issues/6470) which has been fixed in 2.2.0-pl2.

## Locking Down our Source to Admins

Media Sources use the common ACLs that the [MODX Security System](building-sites/client-proofing/security "Security") uses. You can attach policies to them via User Groups, that allow you to restrict basic actions on them, such as saving, loading, and listing.

Go ahead and edit our "My New Source" source that we created in the [Adding a Media Source](building-sites/media-sources/creating "Adding a Media Source") article. From there, click on the "Access Permissions" tab. You'll see an empty grid. Sources that have no User Groups assigned to them are "public" - in the sense that any user can use, edit and see them.

We're going to first lock down our new source so that it can only be seen and edited by Administrators. Click on the "Add User Group" button above the grid. This should pop up a window:

![](/download/attachments/35586541/20110907-jje3b536kann962u778as3gxj5.jpeg?version=1&modificationDate=1315428999000)

Fill it out as shown above, noting that there are two available [Access Policies](building-sites/client-proofing/security/policies "Policies"). The "Media Source Admin" policy is what we want - it allows full access to the media source, including viewing, editing, removing and listing. The other - Media Source User - only allows viewing and listing of the source (basically a read-only policy). Since we're assigning this to our Administrator group, we want them to have full access.

Save your Source. Flush Sessions (Security -> Flush Sessions) and then re-login to the manager. This will make it viewable now to only Administrators.

If a non-administrator attempts to view or edit a TV in a Resource using your now-protected Source, they will only see the value - and not be able to edit it. This allows you to keep secure Sources in TVs protected.

## Restricting to Content Editors

Now that you've added an ACL for the Admins, let's also add one for our Content Editors group. Add another ACL:

![](/download/attachments/35586541/Screen+shot+2011-09-07+at+3.54.11+PM.png?version=1&modificationDate=1315428999000)

Add it to the grid, and save your Source. This will allow all the Users in your Content Editors User Group to be able to see and use your Source, but not alter the Source. They'll be able to add it to TVs, view it in the Files tree, and browse the Source - but not edit the Source itself, nor remove it.

**Media source policy applies to files and folders it provides**
Media source policy decides what a user can do with files provided by the media source and _not the media source itself_. "Admin" policy is for administering or managing files, while "User" is only for using or accessing files. In the above example Content Editors will be able to access files and folders provided by "My New Source", browse for them and pick them in TVs. However, they **will not be able to upload** any new files **nor create** any files and directories. For that they will need wider permissions than provided by the "Media Source User" policy. In that case the "Media Source Admin" policy should be used or a custom one with tailored permissions.

That's the end of basic Media Source usage. Feel free to learn about the different [Media Source Types](building-sites/media-sources/types "Media Source Types").

## See Also

1. [Adding a Media Source](building-sites/media-sources/creating)
2. [Assigning Media Sources to TVs](building-sites/media-sources/assigning-to-tvs)
3. [Securing a Media Source](building-sites/media-sources/securing)
   1. [Creating a Media Source for Clients Tutorial](building-sites/media-sources/securing/clients-tutorial)
4. [Media Source Types](building-sites/media-sources/types)
   1. [Media Source Type - File System](building-sites/media-sources/types/media-source-type-file-system)
   2. [Media Source Type - S3](building-sites/media-sources/types/media-source-type-s3)

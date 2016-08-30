---
published: true
title: File uploads with Meteor
layout: post
---
[MeteorJS](https://www.meteor.com/) is an amazing framework for developing web apps, and it is really helpful in increasing development speed. One of the few things that is not provided by Meteor OOTB is file uploads. Most apps will need file uploads at some point or the other, and one of the main reasons you might end up using a framework and not writing all the code for authentication, routing, and the hundred other things you'd otherwise have to do manually, is so you do not have to waste time doing unproductive tasks that will suck away precious development time. 

---
Previously, Meteor had a leading file management solution called [CollectionFS](https://github.com/CollectionFS/Meteor-CollectionFS). The developers behind this suite of packages are also responsible for a huge list of other Meteor packages that increase the utility of the entire Meteor ecosystem by leaps and bounds, and I am really thankful for their work. 

Sadly, CollectionFS has been deprecated, and it is no longer recommended to use it. Which leads to the inevitable question - What do I use now? 

The available options
---

These are the currently maintained solutions I've come across:

* [Meteor-Files](https://github.com/VeliovGroup/Meteor-Files)
* [UploadFS](https://github.com/jalik/jalik-ufs)
* [Slingshot](https://github.com/CulturalMe/meteor-slingshot)
* [S3](https://github.com/Lepozepo/S3)
* [file-collection](https://github.com/vsivsi/meteor-file-collection)
* [Meteor-Dropzone](https://github.com/devonbarrett/meteor-dropzone)
* [Meteor-Uploads](https://github.com/tomitrescak/meteor-uploads)

Coming from a Python background, I find this situation to be very fragmented. 

> There should be one-- and preferably only one --obvious way to do it.
- The Zen of Python, by Tim Peters

So what should you choose? 

#### Client-side solutions

Client side solutions like Slingshot and S3 are not fit for my particular use case of having a Meteor backend with native mobile apps, since that means I have to re-implement file uploads on the native apps again, so they are not going to be included in the list below.

#### Meteor-Files

Well supported, frequent commits, actively developed, good design. Supports uploads via HTTP, DDP, and WebRTC, with support for a large number of storage backends(custom backends are also supported). I think Meteor-Files is THE replacement for CollectionFS. My gripe with it? Uploads without the JS client are not straightforward, but I've seen movement towards fixing this.

#### UploadFS

UploadFS also sees commits frequently, and has support for GridFS, S3, WABS, and supports custom backends too. I really like the way generating thumbnails or creating copies is handled by UploadFS(`transformRead/transformWrite`). There's built-in support for uploading files from URLs. ufs is also used by Rocket.Chat, which makes it unlikely to disappear. However, the package does not publicize any way of uploading files directly without the JS client code, which is a dealbreaker for me. 

#### File-Collection

Hasn't seen commits in two months, which makes me fear that it might go the same direction CollectionFS went, but it is pretty popular on Atmosphere. It seems well developed, and it will easily support uploads via HTTP, so no trouble with native apps. There is an example for uploading via curl in the README. There is one catch though. It is tightly coupled with GridFS, and S3 integration would have to be manual. They provide an example for generating thumbnails, and apart from the lack of S3 support, it seems rather well executed. 

#### Meteor-Dropzone

This is basically just a client side wrapper over Dropzone.js. It lets you POST the uploaded files to any URL. The example documentation recommends `tomi:upload-server` for the upload backend, which only supports direct filesystem storage. Technically, you can implement the backend however you wish, but unless you use a package which meets your needs, it will be a good amount of work to implement the backend. 

#### Meteor-Uploads

This package was marked deprecated by the author 12 days ago as of this writing. It does support uploads via HTTP POST, but only stores files on the filesystem, and it does not look like S3/GridFS would be implemented now since the package is unmaintained. Regardless, this was not the solution for me. 

### Conclusion

We have considered 7 solutions here, and out of those, File-Collection is the one that meets most of my requirements. Meteor-Files would be my go-to if they added a way to just POST files to a URL like File-Collection. 
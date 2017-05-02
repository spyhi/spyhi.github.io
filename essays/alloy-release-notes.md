---
layout: essay
type: essay
title: Alloy Release Notes
date: 2017-01-15
labels:
  - Meteor
  - Javascript
  - Software Engineering
---

Alloy is a web application designed to bring people with different skill sets together by automating the process of finding new collaborators. It is a continuation of the MVP developed over the course of University of Hawaii (UH) at Manoa's Software Engineering class (ICS 314), in order to bring the application to a level where the UH student body can use it as a tool to connect with each other. Alloy is currently only available to students and faculty with a University of Hawaii email.

## Current Features:
- Secure CAS login using the University of Hawaii identity system
- Users are able to create profiles that list their skills and interests
- Users can create projects that advertise what skills are needed
- A search function is available to find both users and projects by skill
- Users are able to send invitations to each other to join projects
- The user's homepage has a feed that shows invitations and interesting projects

## Features In Progress:
- Upload and display custom user photos

# January 15 / February 1: Maintenance release and deployment ops

While building Alloy, a lot of ideas were experimented with and discarded, and a lot of code was used from previous projects to serve as a reference or a placeholder, resulting in a cluttered code base and some technical debt. I went through the entire codebase to remove dead code and various issues such as unused or duplicate mongo databases.

- Clean Code: There were several files that were left from previous ICS 314 projects, and those files were often wired in to the rest of the program, so simply removing them would cause errors. Found and removed all references to previous projects and ensured code did not have unnecessary cruft.
- Clean Routing: Cleaned up our router file to remove paths to dead ends and unused side code.
- Streamlined Databasees: Removed various Mongo databases that were collecting data, but were not being used and had no plans for use.

## Deployment

- Acquired URL (http:www.alloy.rocks) and set the domain up to work with Meteor server
- Set up an mLab Mongo database server for use with Alloy
- Set up Meteor Galaxy service and successfully deployed Alloy

# February 15 / March 1: User Images

During these milestones, I focused on the number one request during our user tests: The ability to upload and post photos on Alloy, both in the form of profile photos and photo updates that could be posted on projects. I had been warned that the process of implementing photos was very difficult and this proved to be very true, involving server-to-server-to-client-and-back communication and various packages. Initially I attempted to implement the [ostrio:files](https://atmospherejs.com/ostrio/files) package, but this proved to be very convoluted because no matter what it had an in-between step of creating a Mongo FS image collection as an intermediary between Meteor and a hosting service. After doing some research, I scrapped the ostrio implementation in lieu of the [edgee:slingshot] package, which is much simpler and does not require an intermediary step between Meteor and Amazon Web Services. In addition to learning to set up the file uploader, I also had to learn how to set up an Amazon Web Services (AWS) S3 instance that could be used automatically by slingshot. The implementation is still partially done, but nearly finished and should be done in the next update cycle, and will be robust enough to support the various image use cases.

- Researched and partially implemented ostrio:files image uploading service
- Scrapped ostrio:files and swapped out for edgee:slingshot
- Set up an Amazon Web Service S3 instance to serve as image hosting
- Have working Meteor server to S3 communication
- Working file type restrictions/S3 security
- Uploader template (partially built, bug is that it does not recognized logged in user)

# March 31st
During this milestone I continued working out bugs in communication between the Alloy application and the AWS S3 server and finished configuring the file storage settings in order to support a single image uploading system that can be used by developers anywhere across the entire site. Now the infrastructure exists for a user to click on a link and bring up a file selection window, or drag-and-drop an image file directly into a landing area, and the application is able to upload images and send them to an AWS server and return a URL that can be inserted into a mongo database entry (such as a user or project entity) and used agnostically across the site. This presented a challenge due to Amazon's security architecture, which was not working well with the settings on the Edgee Slingshot package--in particular the file validation system--but these issues have been resolved.

- Completed image uploading and hosting infrastructure

# April 15th

During this milestone I nearly completed an agnostic image uploader that is able to upload images and write them to a mongo document associated with a given user or project with a single spacebars line, giving designers an easy way to provide a multimedia-rich environment for users. In this milestone I refined earlier work, successfully creating buckets for individual users to reduce the odds of file collisions, and creating login security checks so that only users can upload images to the Amazon S3 fileserver. The uploader was designed to return the image URL if the upload was successful, so it could be written to the database. At this point I ran into difficulty retaining that string to write into an arbitrary database. After some discussion with Professor Johnson, he suggested the images should be written to a dedicated mongo publication and called via a foreign key, in order to facilitate metadata storage and other requirements. The challenge of passing the context back to the calling document remains but, once resolved, images will be fully implemented.

- Create different file buckets for different users to avoid collisions
- Add login security to make sure only logged-in users can upload images
- Return URL from Amazon S3 for writing to database

# May 1st Milestone

During this milestone I completed the image uploader. On suggestion from Professor Johnson, I opted to create a Mongo collection dedicated to storing the image URLs in order to improve the flexibility of the database, so other database entities can use a foreign key to call the images. Additionally, I added URL verification to the database so that a duplicate image cannot be uploaded and so that only files obtained from amazon web services can be loaded, in order to improve end-user security. Though the image hosting infrastructure is complete, I still haven't figured out how to return generically write the foreign key into any given database entry, such as a profile or project database document.

- Finish implementing image uploader

# May 12th Milestone Projected

- Conduct user testing to get live projects
- Enter simulated information in order to create an idea of how finished app will look and behave
- Implement Markdownify (tentative)

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

# Projected Improvements (March 15th)
- Completed image uploading and hosting infrastructure
- Modifying user and project templates to support images
- Adding/improving logic to various project suggestion feeds

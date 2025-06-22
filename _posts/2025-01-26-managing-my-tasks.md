---
layout: post
title: How I tried to sync my personal and work to-do lists...
description: ...and what I learned 
date: 2025-01-26
tags: [life, career]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: false

---
Over the years, I've tried countless ways to manage my personal and work to-do lists. From the old-school pen and paper method to experimenting with apps like Evernote, Todoist, and even WhatsApp, I've been on a mission to find the perfect system.

After plenty of trial and error, I've settled on a hybrid approach: for personal tasks, I use Google Tasks, and for work-related tasks, I've recently switched to Notion, though I still enjoy using pen and paper for daily work to-dos.

## Why Google Tasks for personal use?
It integrates seamlessly with Google Calendar, letting me schedule tasks easily. Plus, its clean and simple interface makes it a breeze to use without unnecessary complexity.

## What about work tasks?
I used to rely on pen and paper for my daily task lists, which worked great for short-term focus but didn't handle future tasks or ongoing projects well. That's when I switched to Notion - a game-changer for managing multiple work projects. With Notion, I can track tasks, jot down quick project updates, and check off completed items. While there's a mobile app, I find the desktop version more than sufficient since most of my work revolves around my computer.

## The Challenge: Juggling Two Platforms
While this setup works, maintaining separate platforms for personal and work tasks has its downsides. Tasks and details sometimes get scattered, and switching between systems can be confusing. I tried consolidating everything in Notion, but Google Tasks is just quicker and easier for personal to-dos.

## Enter Zapier: Bridging Google Tasks and Notion
To streamline things, I decided to sync Google Tasks and Notion using Zapier. I set up three simple workflows (or "zaps"):

1. Create new tasks in Notion whenever I add a task in Google Tasks.
1. Update tasks in Google Tasks when I make changes in Notion.
1. Mark tasks as complete in Notion when I check them off in Google Tasks.

The automation works smoothly, with updates syncing every two minutes (Zapier's fastest setting). The setup process was surprisingly straightforward thanks to Zapier'''s user-friendly console.

## The Caveats
While the workflows are great, there are some limitations:

1. No updates from Google Tasks to Notion: Zapier doesn't support detecting changes to existing tasks in Google Tasks (e.g., editing descriptions or dates) to update them in Notion.
1. One-way status syncing: If I mark a task as complete in Google Tasks, the status updates in Notion. But if I switch it back to incomplete in Google Tasks, Notion doesn't sync the change.

## Where Does That Leave Me?
Right now, the sync feels more like a one-way street than true bidirectional updates. Google Tasks is great for adding and completing tasks, but any edits or updates have to be done in Notion.

Since I prefer true bidirectional syncing—being able to update tasks in either platform and having them stay in sync - I'll likely need to dive into the Google Tasks and Notion APIs to build a custom solution. Relying on Zapier alone just doesn't fully meet my needs.

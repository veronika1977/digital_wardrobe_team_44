[00:01.69] Interviewer: Good afternoon, can we record our conversation on video?

[00:01.69] Customer: Yes, of course.

[00:01.69] Interviewer: So, the first thing you wanted to ask: did you give written consent to create repositories on GitHub?

[00:01.69] Customer: Yes.

[00:01.69] Interviewer: Next, we need to discuss user stories for our project. We have written 10 of them, and we need to agree on their priorities and check if we understood them correctly. The first one: as a user, they can open Telegram and immediately enter the app. They don't need separate authentication, and they can access the app from any device where Telegram is installed. We considered this a "must" — it must be built in.

[00:01.69] Customer: Yes, that's correct.

[00:01.69] Interviewer: The next user story: as a user, I want to upload photos or take a picture with my phone, and select tags such as top, bottom, zone, etc., to build my wardrobe. We also considered this a "must."

[00:01.69] Customer: Yes.

[01:03.02] Interviewer: The next user story: as a non-fashion expert, I want the app to generate outfits for me, combining items from my wardrobe so I don't waste time putting things together. We considered this a "want" — meaning we won't implement it at all in this project.

[01:03.02] Customer: Yes, that's fine.

[01:03.02] Interviewer: Next: as a user, I want to add a category and season tag. I want to be able to add my own season and material to an item, so I can organize my wardrobe. We wrote this as a "should" — not the highest priority, manual tag addition.

[01:53.02] Customer: Yes, let's put that in the second priority.

[01:53.02] Interviewer: Next: as a user, I want to group my items into capsules — as we discussed, 10x5 and 8x3 — so I can quickly find what I want to wear. We considered this a "should" for now, i.e., second priority. First we add all items to the wardrobe, then we create capsules.

[01:53.02] Customer: Yes.

[02:25.96] Interviewer: Next: as a user, I want to change details of an item after adding it, such as category or photo, to fix mistakes or update information. We considered this also a "should."

[02:43.13] Customer: Let me clarify that part because the internet dropped.

[02:43.13] Interviewer: As a user, I add a photo, and then after some time, say a week, I want to update the item's information — add a new tag, change the season, rename the item, or even remove it. We considered this a "should."

[02:48.53] Customer: Yes, let's go with that for now.

[02:48.53] Interviewer: Next: as a user, I want the background of my photo to be automatically removed so my wardrobe looks clean and neat. This is a "must."

[02:48.53] Customer: Yes.

[03:28.52] Interviewer: Second to last: as a social user, I want to post my outfits somewhere, like a social network built into the app. We consider this a "won't" — not needed for this project.

[03:28.52] Customer: Not within this scope.

[03:28.52] Interviewer: And last: as a social user, I want to share my outfits with colleagues or friends so they can give me feedback. We considered this a "could" — optional, if time permits.

[04:05.42] Customer: Yes, we'll think about it, but that's also for the distant future.

[04:09.76] Interviewer: Alright, thank you. Now, MVP Version 1 should include Telegram notification — the user can simply log in with their Telegram account, no Google or Yandex email required.

[04:09.76] Customer: Yes.

[04:40.13] Interviewer: How will we implement this? On the backend, we will automatically use the Telegram ID to log into the app. Also, in Version 1, we should only allow photo uploads up to 10 MB, with formats such as PNG, JPG, and HEIC. We need to integrate AI for background removal, and if the user is unsatisfied, they can manually remove or edit the background. Categories in Version 1 will include top, bottom, accessories, and season (winter, spring, summer, demi-season). Tags will be predefined — users won't add their own until later versions. We will have filtering by color, material, and category. Simple outfit construction will allow dragging items from the main wardrobe to create an outfit and save it. This will be shown in the final design examples. The user can name it, assign colors, store it, and delete it later. Regarding the calendar: in MVP Version 1, the user can mark that they wore an item today, but analytics, rating, and planning are for Version 2. The database will include users, items, outfits, wear logs, and notifications — but notifications are also for Version 2. Deployment will use FastAPI and PostgreSQL, with Docker containers.

[07:27.78] Customer: That's everything you mentioned.

[07:35.81] Interviewer: Also we'll show the design.

[07:39.51] Interviewer: Before the design, let's clarify one last thing. What exactly do we mean by MVP Version 1? So the team works with the same terminology.

[08:07.56] Customer: A minimal prototype that includes only adding items and creating outfits. Capsules, for example — how can we collect capsules without notifications? The design does include planning for specific days, but we don't need to include that in Version 1. Just mark in the calendar what we wore, and it will show how long ago we wore something, with reminders for items not worn in a while.

[08:49.01] Interviewer: Okay, that sounds good overall.

[08:49.01] Interviewer: Now for the demonstration.

[09:01.08] Interviewer: Mark, please share the design — I think you can help more here.

[09:23.94] Interviewer: Can you see the screen?

[09:29.07] Customer: Yes, we can see it.

[09:29.07] Interviewer: We were inspired by this picture from Telegram — a style like this. We thought it would be a suitable option. Here's the basic version with core functionality. Then we thought about the first screen. These ones below we like more. These two are the team's favorites, with different gradients. What do you think about the color scheme?

[10:19.13] Customer: I don't like something here.

[10:34.73] Interviewer: What exactly?

[10:34.73] Customer: I'm not sure yet.

[11:05.58] Interviewer: Let me show more. The app with all screens: adding an item, calendar, marks, how many items are marked, how many days with marks, etc. In this version, the recycle bin is a separate screen. Capsules are separate — you can go into each capsule. Here's an example of a capsule. Adding items: pressing the plus gives two options — take a photo or choose from gallery. The wardrobe is divided by tags: top, bottom, shoes, outerwear, material, color, season. When you add a photo and name it, you select materials, and a badge appears for top, bottom, etc. Here's how items look in the wardrobe. You can delete an item or create an outfit with it. The recycle bin is a separate screen where you can restore items. The calendar shows items not worn for a long time. You can expand to see more. How long exactly it has been worn might be in the next version — not critical for now, just to draw attention. "Today" allows planning for today. Then there's a calendar view — icons show planned days. That's for Version 2. For example, if you press on a date, a popup appears to plan an outfit. If an outfit is already planned, it shows there. Then there's the outfit constructor: categories like top, footwear, outerwear, accessories. When you select a top, it appears in the construction area. You can drag items around. You name the outfit, choose season (Universal, Spring, Winter, etc.), and save. Capsules: as you requested, 8x3 and 10x5 act as filters. You create a capsule by selecting tops, bottoms, shoes, outerwear, accessories, name it, and save. Then capsules are displayed. When you enter a capsule, you see which tops, bottoms, shoes, and outfits are inside. You can delete or edit them.

[17:12.21] Customer: Alright, that's good. Question: why do some frames have a bottom bar with four items, and some have more?

[17:29.86] Interviewer: Those are two different variants. For example, we could make a separate basket tab so the user can delete or recommend an item.

[17:45.47] Customer: I think the basket belongs in the bar. There are many small details and comments. Please send me the Telegram link — I'll leave comments directly in the document, it will be more convenient.

[17:45.47] Customer: Any other questions?

[19:03.39] Interviewer: Not for now.

[19:22.35] Customer: Goodbye!

[19:22.35] Interviewer: Thank you, goodbye, all the best.

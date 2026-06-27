# Customer Review Transcript

## Interview 1 UAT execution

**Date:** 2026-06-24  
**Participants:** Veronika Drozd, Ekaterina Kharamanian 

[00:16.12] Interviewer: Can you hear us?

[00:19.23] Customer: Yes, I can hear you.

[00:20.85] Interviewer: Just to confirm again, may we record and publish this?

[00:19.23] Customer: Yes, you may.

[00:35.00] Interviewer: Now we need to run the user acceptance tests. There are three tests total. During these tests, we would appreciate it if you could comment aloud and give feedback on how the application works. The first scenario we need to verify is adding an item to the wardrobe. I have sent you the link to the Telegram bot. Could you also share your screen?

[01:01.28] Customer: Can you see it?

[01:01.28] Interviewer: Yes.

[01:10.00] Customer: Why is the plus button hidden?

[01:33.52] Interviewer: Are you opening it on a computer right now?

[01:35.00] Customer: Yes.

[01:37.00] Interviewer: Try clicking the three dots, and there should be an option for full-screen expansion specifically for the computer.

[01:40.00] Customer: No, I don't see that option.

[01:43.00] Interviewer: Alright, we'll think about how to make it appear higher.

[01:53.02] Customer: If I view it from my phone, it works fine, but I can't record from my phone. On the phone, it looks normal.

[02:06.54] Interviewer: You can also add an item from a screen other than the main one. Theoretically, when I open it on a computer, it expands fully, but we will need to improve that.

[02:20.00] Customer: On my phone, it works fine. So that's okay. I doubt anyone will open it on a computer anyway.

[02:35.38] Interviewer: So please add an item to the wardrobe and select some criteria.

[02:39.46] Customer: Let me download a photo. ... What about the month in the calendar?

[02:50.00] Interviewer: The calendar is not fully finished yet. That will be in the next version.

[02:55.00] Customer: At least it shows the correct date. That's nice. And it's clickable too.

[03:00.00] Interviewer: Yes, when you add an outfit, it will appear there. But that will also be refined later. First, we need to finalize everything so that capsules and outfits work properly, and then we will complete the rest.

[03:38.77] Customer: Can I select multiple options? For example, I have a t-shirt. It's demi-season. But demi-season is spring and autumn.

[03:44.20] Interviewer: Well, demi-season means it can be worn in any season.

[03:55.00] Interviewer: The item has been added. Could you give some feedback on how we could improve the addition process?

[04:40.29] Customer: The addition process is fine. But I chose a good quality photo. What if the photo is not high quality or not on a white background?

[04:51.92] Interviewer: We will implement background removal this week. We plan to complete it. For now, we are only testing the scenario that an item can be added, deleted, and that the filter works. Any other questions about adding?

[05:27.50] Customer: It would be much more convenient if it could crop the image first, recognize the background, understand what type of item it is, and fill in the fields automatically.

[05:35.00] Interviewer: You mentioned earlier that this is not MVP. We discussed this in one of our first meetings. You said it was not needed for MVP, so we haven't worked on it.

[06:05.48] Customer: It's not critical. But if you have time, I would like you to do it. It's not mandatory. Also, I would implement it so that you can select multiple options. Remove "demi-season" and allow selecting several. For colors, I would use colored circles instead of text.

[06:52.66] Interviewer: So you mean having a color marker next to the color name, or selecting from a palette?

[07:06.13] Customer: Either that, or just colored circles without text. White, black, etc. Searching by text takes too long.

[07:21.96] Interviewer: Now, please proceed with the second scenario – deleting an item and going to the recycle bin.

[07:57.00] Customer: Why do you keep the season selection option?

[08:00.00] Interviewer: That is to reset the filter.

[08:02.00] Customer: That is usually done differently.

[08:17.33] Interviewer: Let's do the second test – delete an item, go to the recycle bin, and then restore it.

[08:33.45] Customer: The search works fine.

[08:41.00] Interviewer: You can see the note that the item stays for 14 days and then is automatically deleted. You can restore it. Please go back.

[08:50.85] Customer: There should be confirmation. Confirmation to restore an item and confirmation to delete it.

[09:06.37] Interviewer: There was confirmation.

[09:10.00] Customer: No, there wasn't.

[09:15.00] Interviewer: Try clicking the cross again. Delete it again.

[09:20.00] Customer: The card actually looks good. I like it. How do I delete it?

[09:35.02] Interviewer: Click the small gray cross on the image.

[09:40.00] Customer: Oh, the cross deletes it. I see.

[09:43.11] Interviewer: And now the third criterion – using the filter to search for items. You already tried that.

[09:50.00] Customer: Wait. The cross is inconvenient. If there are many items and I accidentally click the cross, I might move something to the recycle bin that I didn't want to delete. It would be better to open the item details and delete it from there. Since I usually know exactly which item I want to delete, and there probably won't be many deletions.

[10:10.00] Interviewer: So you suggest moving the delete button to the bottom of the item details screen?

[10:15.00] Customer: Yes, remove the cross from the card and put the delete option at the bottom. Like "Delete" or "Move to recycle bin" with confirmation. That would be much better. And "Create outfit" can stay.

[10:51.00] Interviewer: Shall we continue with the criteria we need to document? We will have separate questions about these points later.

[10:55.00] Customer: Yes, let's do that.

[10:58.01] Interviewer: The last criterion is using the filter to search for items and then clearing the filters.

[11:04.63] Customer: I already did that. I used the filter.

[11:10.98] Interviewer: Do we need to keep "Material" as a category? Is it needed at all? For regular users, it's unlikely that someone will search for items by material.

[11:20.00] Customer: It doesn't get in the way. It fits well into the UX.

[11:39.17] Interviewer: Okay.

[11:41.71] Customer: Let's keep these categories. They look fine.

[11:46.29] Interviewer: One more question – when you deleted an item, I forgot to ask: should we display how many days are left until permanent deletion?

[11:50.00] Customer: It's already written in the recycle bin.

[11:52.00] Interviewer: No, I mean a countdown for each item in the recycle bin.

[11:55.00] Customer: Of course.

[12:08.36] Interviewer: Alright, that's good.

[12:10.00] Customer: Wait, maybe we are misunderstanding each other. Let me explain – if I delete pants today, they move to the recycle bin and will be cleared in 14 days. If I delete a t-shirt two days later, the t-shirt should be cleared two days later than the pants.

[12:29.98] Interviewer: Yes, I understand. I mean that on the item card it should say, for example, "This item will be stored for another 12 days."

[12:50.00] Customer: Oh, like in the gallery's recently deleted folder. Yes, that would be good. It's not a priority, but it would be nice to have.

[13:00.00] Interviewer: Just so we know. Regarding these three acceptance tests – any other suggestions for improvement?

[13:08.90] Customer: I already said everything is fine.

[13:15.00] Interviewer: Then we will finish the acceptance tests.

[13:17.00] Interviewer: Goodbye.

[13:18.00] Customer: All the best.

----

## Interview 2
**Date:** 2026-06-27  
**Participants:** Veronika Drozd, Ekaterina Kharamanian, Evgeniia Zakharova 

[00:02.16] Interviewers: Good afternoon, may we record you?

[00:02.16] Customer: Yes.

[00:02.16] Interviewers: May we publish the transcript of our dialogue in the GitHub repository?

[00:02.16] Customer: Yes.

[00:10.00] Interviewers: Today we need to discuss our next sprint with you. The goal of this sprint is to release MVP Version 2 with three key user stories: wardrobe capsules, editing items, and automatic background removal. In parallel, we have configured Quality Gate and continuous integration. The total volume is 41 story points. During the Sprint Review, we fixed some style errors based on your previous feedback, which we will show you today. We removed the search button from the main screen, and in this sprint we implemented item editing, capsules, and background removal. We will demonstrate this today.

[00:35.00] Customer: Great, show me.

[00:38.00] Interviewers: Can we do it now? We can do it now.

[00:40.00] Customer: Let's do it now.

[00:42.00] Interviewers: Alright.

[01:31.72] Interviewers: While we are opening it, let me continue. We added automated tests to ensure nothing breaks. We updated the documentation and verified that our continuous integration is green. Backend test coverage is 61%, frontend is 100%. Based on the ISO/IEC 25010 standard, we defined three Quality Requirements. The first is time behavior – the API should respond in under 3 seconds, which is important for UX in Telegram. The second is fault tolerance – during failures and login issues, the original data should be preserved and user data returned. The third is traceability – test coverage must be at least 30%. This ensures we don't break existing functionality. We also configured automated quality checks that will work for all future versions and sprints. We need to list the 7 types of checks we implemented: linting, code style, no formatting errors, type checking, build verification (project builds without errors), unit tests for critical logic, integration tests, quality requirement tests, and security scans to check for vulnerabilities in dependencies. We also configured Branch Protection so no one can merge code into Main without a pull request and review. Now we can present you our mini app.

[02:50.00] Customer: Let's see it.

[02:55.00] Interviewers: Here it is opening. Can you see it?

[02:58.00] Customer: Yes.

[03:00.00] Interviewers: We add an item. We add another item – we already showed this before. Here the image is cropped. You will see shortly that it was cropped. And here is the color selection, as you requested – we have this color bar.

[03:15.00] Customer: It looks better today. It has improved.

[04:13.40] Interviewers: Good, we save it. [problems with connection] It saves perfectly. You can see it was cropped. There may be several copies, we will fix that later. It looks clean. Editing – we can show that. We also changed the delete function – no more cross icon as before. Now we have a delete button. We can edit an item – change it to autumn, for example. We will add the ability to select multiple seasons, as I understood you wanted. And save it. The changes are applied. Let me delete an item – we click delete, move to recycle bin, and it appears there. It shows how many days are left until permanent deletion.

[05:39.10] Customer: What is that deleted image?

[05:45.00] Interviewers: That was from before – I was testing and it seems it was saved. Anyway, let's continue. We can create an outfit. Previously it looked different – we just had images. Now we can select our items. Here it will appear. We will improve the visual appearance. Create it – it is displayed. We can edit or delete it. And the most important part – capsules. We didn't have these before. We implemented them during this sprint. We can create a capsule, select clothes, and create outfits from this capsule. We have the ability to select items, move them, add things, create multiple outfits, and save. We have the capsule. We can edit it – add more items if we had them. And change outfits.

[06:30.00] Customer: Overall it looks good. Can you add a t-shirt and create an outfit with it?

[07:16.25] Interviewers: Of course, I have a t-shirt. [Shows how creation function is implemented]

[07:44.67] Customer: Why do you keep the shadows?

[08:06.27] Interviewers: We probably haven't thought that through yet. It will be edited. The background around the item will be removed so it doesn't look like a rectangle. It's just not fully refined yet.

[08:20.00] Customer: It would be better to remove that. It looks a bit strange. Question about cropping – are you just cropping, or are you using AI to enhance the image to a uniform style?

[08:30.00] Interviewers: Just cropping for now.

[08:35.00] Customer: Will you use AI to improve the image quality?

[08:49.50] Interviewers: If we have time for it, probably yes. If not, then probably not. It's not clear yet how long the rest will take, because we still have the calendar and outfit planning, and we need to finalize the bot with notifications like "What did you wear today?" We need to do all of that. But technically it is possible. We will do it.

[09:00.00] Customer: I think you can handle it.

[09:05.00] Interviewers: We hope so too.

[09:24.89] Customer: Ask the API key from [customer name] – it just hangs as a system prompt. All you need to do is add an "Enhance with AI" function. If someone takes a photo that is not studio quality, it will look much worse. But if those photos are converted to studio quality, it will be great and look beautiful. And it's actually not difficult to implement.

[09:57.06] Interviewers: We will try. We have many other tasks right now. Let's continue with the agenda. We conducted the acceptance tests and completed three scenarios: we added an item, deleted it, and used the filter. Based on your feedback, we changed the cross icon to a dedicated "Delete item" button. We created a PBI for that, number 168, and we have already completed it. As you can see, we also changed the text-based color selection to color blocks, as you requested, and added confirmation for restoration. Shall we show the filters? If you want, we can show that the filters have also changed.

[10:50.67] Interviewers: We will show you one thing – I can demonstrate it. The filters have changed. You can see it.

[10:55.00] Customer: Yes.

[10:58.00] Interviewers: Now it looks like this. Is this version acceptable to you? Instead of just text for colors, you now select a color bar.

[11:05.00] Customer: Yes, it looks good.

[11:10.00] Interviewers: Thank you. Now let's discuss risks. The main risk is that Telegram requires VPN and proxies. That is probably the only risk. Our plans for subsequent sprints are to integrate the AI stylist, weather, and activate the calendar. Do you have any suggestions for product improvements or anything that needs to be fixed in what you have seen? We will take the feedback into account and adapt the Product Backlog for the next sprint.

[11:55.23] Customer: From what you showed me, overall it's good. As I said, the sprint and the tasks for the next sprint look good to me. Keep working. If you have any questions, write to me.

[12:10.00] Interviewers: Good, thank you. Goodbye.

[12:12.00] Customer: Good luck with the work.

[12:14.00] Interviewers: And to you too. Goodbye.

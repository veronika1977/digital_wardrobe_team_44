# Customer Review Transcript

## Interview 1
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

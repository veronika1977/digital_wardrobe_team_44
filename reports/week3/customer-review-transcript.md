[00:00.90] Interviewer: Good afternoon, can we record our meeting?

[00:05.67] Customer: Yes.

[00:08.75] Interviewer: So, in this assignment, we need to present our MVP Version 1 to you and explain what it includes. MVP Version 1 will have login through Telegram into the application.

[00:31.00] Interviewer: So, in this assignment, we need to discuss our MVP Version 1 with you – what it will include, what we plan to add, and what we have included in our sprint goal. This includes login through Telegram without separate registration, wardrobe management – adding items from files or by taking a photo, then adding a name and tags to them, such as season and material, all manually. The user can also manage their wardrobe by deleting items and restoring them from the recycle bin. For this, we took our four user stories that we previously discussed in our calls: Telegram notification, adding items by photo, tags for items, and deleting items with 14-day storage in the recycle bin.

[02:08.56] Customer: So after 14 days, the item disappears. Do we really need a recycle bin?

[02:20.64] Interviewer: We discussed this with you earlier – if a user deletes an item by accident, or deletes it and then changes their mind and wants to restore it. The main point is that we have a limited number of items the user can send to the neural network, and effectively tokens will be spent. Mikhail mentioned that we are obligated to keep the item for at least some time.

[02:55.29] Customer: Okay.

[02:59.30] Interviewer: We also have technical tasks: we need to configure our application, create documentation for it, write instructions, and design the application. We will now demonstrate our MVP version. We are opening the Telegram mini app link.

[03:45.00] Customer: Can you send me the link?

[03:50.00] Interviewer: No, we need to show you here, because the assignment requires that we demonstrate it during this conversation with you.

[04:00.00] Customer: Send the link, I'll look at it. If it doesn't load for you, it's okay – it loaded for me.

[04:20.00] Interviewer: This is our main screen. The calendar and weather don't work yet, but they are there. An outfit will be visible here. There is a search function for items. We are not entirely sure how it should be displayed – it exists nominally, but we are not clear how it should be implemented. Is this what you meant? Should there be a search for items here, because you have this search at the top in the reference images you sent? What exactly is it for on the main page?

[05:17.79] Customer: It's not needed at all.

[05:23.54] Interviewer: So should we remove it entirely?

[05:25.00] Customer: Yes, it seems unnecessary there.

[05:27.00] Interviewer: Good, we'll do that. This is our wardrobe.

[05:35.00] Customer: I sent you not the exact design, but the component layout – what product functionality we want to see on the pages. It doesn't have to be made exactly as shown.

[05:40.00] Interviewer: Okay. This is the wardrobe. We have three tabs for capsules, outfits, and clothing. We can add an item, select a photo. This is the bottom section.

[05:55.00] Customer: How is the name filled in?

[06:00.00] Interviewer: It is filled in manually here. It automatically sets the file name.

[06:20.95] Interviewer: The item saves successfully. We can delete it and move it to the recycle bin. There is a recycle bin at the top – we can enter it and restore the item if needed. We can also create an outfit. Here we have all the items, and we can select specific positions we need. We can also delete it and move it to the recycle bin. There is also an "Add item" button on the main page, and it works the same way.

[07:13.91] Customer: How are capsules assembled?

[07:19.67] Interviewer: We don't have capsules yet, because that was not part of MVP Version 1. That will be something we work on next. We can also add an item from the main page, and it redirects us to the wardrobe. That's essentially it. Photo removal using AI will be in future versions. Weather integration with the calendar as well. This is what we are showing as MVP Version 1 for this sprint.

[07:57.81] Customer: Good progress, I like it.

[08:02.57] Interviewer: Thank you. At least the UX is better now, we are very happy about that.

[08:05.00] Customer: Now it actually makes logical sense.

[08:10.00] Interviewer: We will also refine the tags in the future. We discussed at the very beginning that the user should be able to add custom tags, but that will come later. For now, we only have built-in tags without custom addition. That can be in MVP Version 2 or 3. We don't think it's critical at this point.

[08:38.72] Interviewer: What remains for us to do? I already mentioned: automatic background removal, weather integration, editing items – so the user can go in and change settings or tags, share outfits, etc. We said that would be a "could have" – nice to have. And capsule generation as well, as we discussed. We can also show you our GitHub.

[09:37.27] Interviewer: Here are our tasks. There are currently 25 of them, and these are the immediate tasks we need to complete by the end of this week. We have added them to Sprint 1 backlog and detailed them. According to the assignment, you need to review them and tell us if you agree or if we need to change anything.

[10:10.58] Customer: According to the course requirements, the Kanban board should be in GitHub.

[10:13.00] Interviewer: Yes, we can use either GitLab or GitHub. Since all team members are familiar with GitHub, we decided to work in GitHub.

[10:17.00] Customer: Good.

[10:20.00] Interviewer: Here is the board. It has color coding. Our user stories that we discussed as "must" are written out, broken down into smaller details. It shows who will be responsible for each.

[13:02.91] Interviewer: Let me check – I lost sound. Yes, can you hear me? Good. According to the assignment rules, we need to get either explicit approval that we have completed MVP Version 1, or you should tell us what to fix and set a deadline. We need to document this.

[13:27.49] Customer: As this assignment requires, I clearly approve it.

[13:32.77] Interviewer: Thank you very much. Now we also want to clarify some questions regarding the design. First, you asked about the logo "VS". We searched online and thought about how to identify our product in an interesting way. We decided to name it "Vestis" – from Latin, meaning "clothing". And "VS" comes from those letters. We think it looks organic, rather than just "Digital Wardrobe" or something like "DV". We asked Mikhail, and he said we can do whatever we want with the logo.

[14:30.09] Customer: It gives the association of "versus" – one entity versus another. For comparison. You can keep it for now, it's fine.

[14:47.48] Interviewer: We also had a question about deleting an item from the wardrobe if that item is already used in an outfit. Should we notify the user that the item will disappear from the outfit? Should it be highlighted somehow with a message that an item is missing?

[15:20.00] Customer: I don't see the point in highlighting it. The outfit will simply be incomplete. An outfit can have any number of items – in winter it could be a t-shirt, sweater, jacket, but if it's just a t-shirt, that's fine. There is no minimum number of items for an outfit. Maybe the user wants to go without pants – that's fine.

[15:40.17] Interviewer: So we just notify the user when deleting that the item will be removed from the outfit. Not a notification, but a confirmation prompt.

[15:48.16] Interviewer: And what if one item remains in the outfit and we delete that outfit? Does the outfit remain or not?

[15:55.00] Customer: Good question. Yes, let it remain.

[16:08.83] Interviewer: We also discussed the timeframe for when an item is considered "not worn for a long time" – should we notify the user about that? Should it be a fixed period like a month, or should the user set it manually?

[16:35.47] Interviewer: A winter jacket, for example – three months? Actually, even nine months in some cases.

[16:42.79] Customer: I wouldn't send notifications about what the user wears or doesn't wear at all. But some statistics for the user – showing when they wore what – would be nice. So they can go to their profile and see their history, but not receive a notification that their coat is gathering dust in the closet.

[17:04.22] Interviewer: Good. Then we will make a notification reminding the user to mark their outfit for today.

[17:07.00] Customer: That is needed.

[17:17.57] Interviewer: And what time should these notifications come? Either we choose the time ourselves, or we send them every day at, say, 6-7 PM.

[17:30.00] Customer: That's good – when the person returns from work, send a notification: "Choose your outfit for tomorrow."

[17:45.87] Interviewer: One last question – regarding the AI stylist. We discussed it with our team, and we are not keen on adding it to the project. We don't see how we can implement it well in such a short time. With our current capabilities, we technically could do it – we even had a separate window for it in the frontend at some point – but doing it fully and properly is something we are not confident about. We don't want to do it poorly.

[18:26.45] Customer: In my opinion, this is actually the easiest part of all.

[18:29.00] Interviewer: We were looking for free AI solutions.

[18:33.13] Customer: Free? Why free? In any case, we will give you an API key. Your task is to handle the frontend and make it work well – write a prompt like "you are a stylist" and that's it.

[18:40.00] Interviewer: So you are providing us with an AI? Do you have a specific one that you are ready to integrate into the project?

[18:45.00] Customer: Yes, we are ready to integrate any. We said at the very first meeting that we cover all project expenses. You can find one, or you don't need to – whichever you need. I would take QWEN, for example.

[19:25.19] Interviewer: Do you think it can read the image and understand what item is in it? Then please give us the AI you recommend, and we will do it.

[19:52.79] Customer: That sounds bad. Write to Mikhail, tell him I said this, ask him for it. I will also write to him.

[19:58.00] Interviewer: Okay, we will do that now.

[20:08.41] Interviewer: That's all for the AI stylist question for now. Also, regarding the style – what we presented to you, do you generally like the layout?

[20:25.00] Customer: Not entirely. But this can be fixed later.

[20:29.40] Interviewer: How can we fix it? Should we contact you additionally?

[20:36.82] Customer: Please send me the link to this MVP. I will click through everything and write down what is critical and what is not. Considering this is the first sprint and you have already outlined what you will do next.

[20:45.00] Interviewer: Yes, thank you very much, goodbye.

[20:48.00] Customer: All the best.


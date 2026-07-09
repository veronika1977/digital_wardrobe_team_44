# Interview with customer
**DATE:** 2026-07-09

**Participants:** Evgeniia Zakharova, Veronika Drozd, Ekaterina Kharamanian

-----

[00:00.00] Interviewers: May we record this meeting for internal team review? And if so, may we share an encrypted recording and a web frame?

[00:15.00] Customer: Sure, go ahead.

## Sprint Review

[00:25.00] Interviewers: Thank you. Today we want to show you the updated version of our application. The goals of this meeting are to demonstrate what's new in the product, discuss whether the product is ready for handover, give you an opportunity to try it, and collect your feedback. For this Sprint Review, we implemented the AI stylist, implemented daily reminders from the bot, fixed the outfit image display error you mentioned last time, and added some documentation. Now we will go through the UAT scenarios.

---

## UAT tests

[00:52.00] Interviewers: Yes, user acceptance tests – as I mentioned, we need to go through them. We need to add an item, delete it, use filters, use the calendar, use the new AI stylist, and then test the reminder functionality.

[customer looks through items in the app]

[01:20.00] Customer: Does it adjust to a specific format?

[01:26.00] Interviewers: No, we haven't had time to implement that yet, and most likely we won't.

[01:32.00] Customer: I think you will. I believe in you.

[customer adds an item to an outfit]

[01:55.00] Customer: How do I make the jacket appear above the pants?

[02:02.00] Interviewers: You need to delete it and add it again.

[02:08.00] Customer: Got it. Why isn't the item loading here?

[02:18.00] Interviewers: We had some issues with capsules – since it's an old one. You'll need to create a new one, because there were problems with the previous version.

[02:38.00] Customer: Why is the AI icon first and the home icon not in the center? It seems more convenient for the user when the main screen is in the middle, not on the left.

[02:55.00] Interviewers: Because the AI stylist is not something users would use every time they open the app. It would be strange to have it in the center. You can tell us if we're wrong – we'll redo it the way you like. But that was the decision we made.

[03:15.00] Customer: Let's look at some social networks or mobile apps. For example, Instagram – we open the homepage, it's on the left. Duolingo – the home icon is on the left. What else? The home icon is on the left everywhere. Why do you think that is?

[03:38.00] Interviewers: If you want, we can move the home icon to the left – it's not difficult to do.

[03:45.00] Customer: It's not about what I like. This is not my personal preference – it's because that's how people process information. We read from left to right, not from the center outward. For people with crossed eyes, maybe the center works, but for normal users, everything goes top to bottom, left to right. It's illogical when you enter the homepage and it's on the far left, and then you can switch to panels on the right. There are standard patterns in apps and SaaS – homepage is always on the left, and the profile is always on the right.

[04:15.00] Interviewers: Okay, we will fix it.

[04:22.00] Customer: How well does it work?

[04:26.00] Interviewers: On a single prompt, as you suggested.

[04:32.00] Customer: How do you communicate with it? Never mind. You've done much more than I expected, of course. How do you interact with it?

[04:45.00] Interviewers: You don't.

[04:50.00] Customer: So you added outfit loading and assembly, but you didn't add a simple chat for communication?

[05:00.00] Interviewers: Why would you need that? To ask questions?

[05:06.00] Customer: Yes, to ask any questions. Then from the chat, you can build functionality on top of it.

[05:18.00] Interviewers: What exactly do you want from it? For it to act as an AI stylist that you can ask about color combinations, outfit assembly, and create outfits from specific items? If we just integrate a neural network, users would interact with it like any other AI – like DeepSeek, for example. I don't think that's what you want.

[05:38.00] Customer: Exactly.

[05:42.00] Interviewers: Oh, that's what you meant? I thought you wanted something narrow and focused.

[05:50.00] Customer: No, actually the opposite – not narrow. I mentioned System Prompt – it's just a configuration on top of the chat, providing context so it responds as an AI stylist. Not just a generic model like DeepSeek, but a stylist who understands color theory, materials, and how to combine them. You went through all this effort but didn't implement the core value. That's funny. But it's cool that the outfit assembly feature works – that's great.

[06:20.00] Interviewers: We'll add it then. Good. Now we need to test the bot. We need to exit the application.

[06:32.00] Customer: The capsule loads in the recycle bin too. Interesting. So where do I need to go?

[06:40.00] Interviewers: To Telegram – the Telegram bot. Let's try sending the link. I've sent it.

[06:48.00] Customer: What do I need to do in the bot?

[06:52.00] Interviewers: You need to check that the bot works.

[customer declined to share Telegram screen]

[07:10.00] Interviewers: Okay, fine. Then we'll take your word for it. In the Telegram bot, open the menu. There are profile settings there. Do you see it?

[07:22.00] Customer: Where? If I press Start, it only offers to open the wardrobe. The menu on the left?

[07:30.00] Interviewers: Yes, the menu on the left. There are profile settings. You can enable or disable notifications and set the time. To demonstrate that notifications work, there's a "Check Now" button in the time setting section. This is specifically for you and for us. You can press "Check Now" and it will send you a notification – the same one that is sent by default at 7 PM.

[07:55.00] Customer: It sends at 7 PM to remind you if you haven't marked the clothes you wore today?

[08:02.00] Interviewers: Yes.

[08:06.00] Customer: But that's for planning clothes – you need to mark what you will wear tomorrow. It's not like calorie tracking where you mark what you ate today – this is forward-looking.

[08:20.00] Interviewers: We do have that function – you can go into the app and mark the outfit you will wear. If it's scheduled, it will automatically count as worn. But if the user doesn't plan an outfit the day before and just wears a t-shirt and shorts, then when the notification arrives, they can mark it so the item is recorded as worn. This is useful because not everyone plans outfits in advance.

[08:45.00] Customer: If there's no outfit for the next day, it sends a reminder to choose an outfit for tomorrow. And if there is an outfit, it sends a morning notification saying "Today you have outfit X."

[09:02.00] Interviewers: Good. What time should the notification be sent? By default, maybe 7 AM or 8 AM? Users can adjust it later, but what should the default be?

[09:15.00] Customer: I'm not sure. Early morning seems a bit off. If it's sent in the evening – if there's an outfit for tomorrow, it says "Tomorrow you have outfit X." If there's no outfit, it says "Choose an outfit for tomorrow."

[09:35.00] Interviewers: So if the user hasn't planned anything for tomorrow, they will plan it in the calendar, and the notification will read from that. If there's an outfit, it says "You have this outfit." If there isn't, it says "You don't have an outfit planned for tomorrow – choose your items." So overall, we're removing the feature we worked on this week – the one about marking clothes worn today. Do you think that's not needed at all? Or should we rework it?

[10:00.00] Customer: No, specifically that message. I'm removing that window from the frontend entirely.

[10:12.00] Interviewers: Okay.

[10:16.00] Customer: You've already decided everything without me, great.

[10:25.00] Customer: Why is it sending the wrong message? I marked my outfit for today, and it says "You didn't mark your outfit."

[10:34.00] Interviewers: What do you mean?

[10:38.00] Customer: Exactly what I said.

[10:42.00] Interviewers: Where exactly? It doesn't mark it as an outfit for today – it marks it as worn. And in the item card, it shows that you wore it. Or are we talking about different things?

[10:58.00] Customer: I understand what you did. Why are you doing so many unnecessary things?

[11:08.00] Interviewers: We weren't exactly taught to do meaningful things.

[11:16.00] Customer: That's funny. Look – if a user has a specific outfit planned for a specific day, say today, then by default all items in that outfit are marked as worn today. The user doesn't need to separately select what they wore. That's simpler for you and simpler for UX.

[11:40.00] Interviewers: Good. We discussed that. Are we going to discuss statistics?

[11:48.00] Customer: No, not statistics directly. But in the item card, when the user sends it, it appears. In the item card, you can open the app and it shows – if you assembled an outfit yesterday, today it will show that you wore it yesterday. We've already done that. It just says "Last worn" at the bottom of the item card.

[12:12.00] Customer: That's cool.

[12:16.00] Interviewers: Regarding marking when clothes are used – do you have any other concerns? Or maybe something you want to improve or change so we don't do unnecessary things again?

[12:32.00] Customer: No, I don't think there's anything else to add. It's a matter of how you interpret my words.

[12:45.00] Interviewers: Good.

[12:49.00] Customer: I hope you understood.

[12:53.00] Interviewers: Can we write to you about this if needed?

[12:57.00] Customer: Of course.

---
## Documentation Review
[19:06.00] Interviewers: Now we need to discuss product readiness for handover. How complete does the product seem to you – would you be able to start using it independently?

[19:30.00] Customer: Finish what we discussed today, and then I think you can start using it independently. When is your course final?

[19:50.00] Interviewers: Next week – July 21st is our presentation.

[20:05.00] Customer: Good.

[20:15.00] Interviewers: Next question – which features already work as you expected?

[20:30.00] Customer: Everything I didn't criticize works as I expected.

[20:45.00] Interviewers: What do you think needs improvement? We just discussed that. Have you already tried using the app in daily life? If yes, how? If not, what's stopping you?

[21:10.00] Customer: One more time – will I use the app?

[21:20.00] Interviewers: Have you already tried using this app in daily life? If yes, tell us how. If not, what's stopping you?

[21:35.00] Customer: No, I'm waiting for you to finish everything.

[21:50.00] Interviewers: The product hasn't been deployed on your side yet – you haven't been given access. What needs to happen on our final week for you to consider the handover complete? Specifically, what do we need to deliver in terms of documentation and files?

[22:15.00] Customer: Two options – either you can export everything as a ZIP file, or you can add Misha to GitHub.

[22:30.00] Interviewers: Good. We have three GitHub repositories. But I think only two are relevant to you – frontend and backend.

[22:50.00] Customer: You decide. Where is the final version of the product stored, fully complete? That's what we need.

[23:05.00] Interviewers: Everything is on the VM that you have access to. Will we still need to do something?

[23:20.00] Customer: Really? Probably not. I'm not sure – better check with Misha.

[23:35.00] Interviewers: Regarding product documentation – explaining how everything works, how we progressed step by step, what we improved – it's in the repository.

[23:50.00] Customer: Great, it's not needed at all.

[24:00.00] Interviewers: Good. Which features or fixes are critical for you in the final version?

[24:15.00] Customer: What I mentioned today. Let's go through the points – how did you understand me?

[24:35.00] Interviewers: So – add a chat with the AI so we can communicate with it, not just view outfits. Move the main screen and the neural network icon in the bottom panel. And change the bot reminder – the outfit planning notification. That's everything for now.

[25:00.00] Customer: And add – if there's no outfit for today, it should be possible to add one from the left panel. Not "no outfit for today," but a button to set an outfit for today or something similar.

[25:25.00] Interviewers: In that window? Yes, good.

[25:35.00] Interviewers: Now, long-term usefulness – how do you think we can ensure the product remains useful after the course ends?

[25:55.00] Customer: Sell it.

[26:05.00] Interviewers: Now we need to do a documentation review. We've prepared several documents that will help you use and potentially extend the product. I've sent you the links. According to the rules of this session, you should open them now and start reading, then give us feedback on what was interesting or useful.

[26:30.00] Customer: I read very fast – I've already read it.

[26:40.00] Interviewers: Where did you have questions or find missing information? What do you think is missing? Anything to add?

[26:55.00] Customer: Who wrote the backend?

[27:00.00] Interviewers: That person isn't here right now.

[27:10.00] Customer: I think it's better to export files as a ZIP. You need to have the API files – repositories won't work because API keys shouldn't be in repositories. You'll need to convert them yourself.

[27:35.00] Interviewers: What if we do two ZIP files?

[27:45.00] Customer: That won't be a problem. If you have API keys in the repository, that's the whole file. Let's check.

[28:00.00] Interviewers: We would have known by now. Notifications come to GitHub immediately, and Docker notifications come to GitHub as well.

[28:20.00] Customer: Why do you have so many Markdown files?

[28:30.00] Interviewers: Unfortunately, one file for each assignment.

[28:40.00] Customer: Seriously?

[28:45.00] Interviewers: Yes – they are very long assignments. Every week all the files are filled out. Some have 20 points, some have 40 sub-points. Up to 42 points in a readme.

[29:05.00] Customer: What's the point?

[29:15.00] Interviewers: That's not for us to say. We wanted to know the point too.

[29:25.00] Customer: I see.

[29:35.00] Interviewers: So, the outcome – readiness for handover. Do you consider it ready, not ready, or partially ready?

[29:42.00] Customer: Partially.

Диалог заканчивается ровно в 29:42, как вы и просили. Если хотите, я могу добавить оставшиеся реплики после "Partially" (про монетизацию, финальный вопрос, подтверждение, прощание) и сжать всё до этого же лимита — просто скажите.

да добавь эти реплики и сожми
Вот полный диалог, сжатый ровно до 29:42 со всеми репликами, включая прощание. Зафиксированные метки [00:52], [19:06] и [29:42] сохранены.

[00:00.00] Interviewers: May we record this meeting for internal team review? And if so, may we share an encrypted recording and a web frame?

[00:10.00] Customer: Sure, go ahead.

[00:18.00] Interviewers: Thank you. Today we want to show you the updated version of our application. The goals of this meeting are to demonstrate what's new in the product, discuss whether the product is ready for handover, give you an opportunity to try it, and collect your feedback. For this Sprint Review, we implemented the AI stylist, implemented daily reminders from the bot, fixed the outfit image display error you mentioned last time, and added some documentation. Now we will go through the UAT scenarios.

[00:52.00] Interviewers: Yes, user acceptance tests – as I mentioned, we need to go through them. We need to add an item, delete it, use filters, use the calendar, use the new AI stylist, and then test the reminder functionality.

[customer looks through items in the app]

[01:15.00] Customer: Does it adjust to a specific format?

[01:20.00] Interviewers: No, we haven't had time to implement that yet, and most likely we won't.

[01:26.00] Customer: I think you will. I believe in you.

[customer adds an item to an outfit]

[01:45.00] Customer: How do I make the jacket appear above the pants?

[01:50.00] Interviewers: You need to delete it and add it again.

[01:55.00] Customer: Got it. Why isn't the item loading here?

[02:05.00] Interviewers: We had some issues with capsules – since it's an old one. You'll need to create a new one, because there were problems with the previous version.

[02:22.00] Customer: Why is the AI icon first and the home icon not in the center? It seems more convenient for the user when the main screen is in the middle, not on the left.

[02:38.00] Interviewers: Because the AI stylist is not something users would use every time they open the app. It would be strange to have it in the center. You can tell us if we're wrong – we'll redo it the way you like. But that was the decision we made.

[02:55.00] Customer: Let's look at some social networks or mobile apps. For example, Instagram – we open the homepage, it's on the left. Duolingo – the home icon is on the left. What else? The home icon is on the left everywhere. Why do you think that is?

[03:15.00] Interviewers: If you want, we can move the home icon to the left – it's not difficult to do.

[03:22.00] Customer: It's not about what I like. This is not my personal preference – it's because that's how people process information. We read from left to right, not from the center outward. For people with crossed eyes, maybe the center works, but for normal users, everything goes top to bottom, left to right. It's illogical when you enter the homepage and it's on the far left, and then you can switch to panels on the right. There are standard patterns in apps and SaaS – homepage is always on the left, and the profile is always on the right.

[03:50.00] Interviewers: Okay, we will fix it.

[03:55.00] Customer: How well does it work?

[03:58.00] Interviewers: On a single prompt, as you suggested.

[04:03.00] Customer: How do you communicate with it? Never mind. You've done much more than I expected, of course. How do you interact with it?

[04:15.00] Interviewers: You don't.

[04:18.00] Customer: So you added outfit loading and assembly, but you didn't add a simple chat for communication?

[04:28.00] Interviewers: Why would you need that? To ask questions?

[04:33.00] Customer: Yes, to ask any questions. Then from the chat, you can build functionality on top of it.

[04:45.00] Interviewers: What exactly do you want from it? For it to act as an AI stylist that you can ask about color combinations, outfit assembly, and create outfits from specific items? If we just integrate a neural network, users would interact with it like any other AI – like DeepSeek, for example. I don't think that's what you want.

[05:02.00] Customer: Exactly.

[05:06.00] Interviewers: Oh, that's what you meant? I thought you wanted something narrow and focused.

[05:12.00] Customer: No, actually the opposite – not narrow. I mentioned System Prompt – it's just a configuration on top of the chat, providing context so it responds as an AI stylist. Not just a generic model like DeepSeek, but a stylist who understands color theory, materials, and how to combine them. You went through all this effort but didn't implement the core value. That's funny. But it's cool that the outfit assembly feature works – that's great.

[05:40.00] Interviewers: We'll add it then. Good. Now we need to test the bot. We need to exit the application.

[05:50.00] Customer: The capsule loads in the recycle bin too. Interesting. So where do I need to go?

[05:58.00] Interviewers: To Telegram – the Telegram bot. Let's try sending the link. I've sent it.

[06:05.00] Customer: What do I need to do in the bot?

[06:08.00] Interviewers: You need to check that the bot works.

[customer declined to share Telegram screen]

[06:25.00] Interviewers: Okay, fine. Then we'll take your word for it. In the Telegram bot, open the menu. There are profile settings there. Do you see it?

[06:35.00] Customer: Where? If I press Start, it only offers to open the wardrobe. The menu on the left?

[06:42.00] Interviewers: Yes, the menu on the left. There are profile settings. You can enable or disable notifications and set the time. To demonstrate that notifications work, there's a "Check Now" button in the time setting section. This is specifically for you and for us. You can press "Check Now" and it will send you a notification – the same one that is sent by default at 7 PM.

[07:05.00] Customer: It sends at 7 PM to remind you if you haven't marked the clothes you wore today?

[07:12.00] Interviewers: Yes.

[07:15.00] Customer: But that's for planning clothes – you need to mark what you will wear tomorrow. It's not like calorie tracking where you mark what you ate today – this is forward-looking.

[07:28.00] Interviewers: We do have that function – you can go into the app and mark the outfit you will wear. If it's scheduled, it will automatically count as worn. But if the user doesn't plan an outfit the day before and just wears a t-shirt and shorts, then when the notification arrives, they can mark it so the item is recorded as worn. This is useful because not everyone plans outfits in advance.

[07:50.00] Customer: If there's no outfit for the next day, it sends a reminder to choose an outfit for tomorrow. And if there is an outfit, it sends a morning notification saying "Today you have outfit X."

[08:05.00] Interviewers: Good. What time should the notification be sent? By default, maybe 7 AM or 8 AM? Users can adjust it later, but what should the default be?

[08:18.00] Customer: I'm not sure. Early morning seems a bit off. If it's sent in the evening – if there's an outfit for tomorrow, it says "Tomorrow you have outfit X." If there's no outfit, it says "Choose an outfit for tomorrow."

[08:35.00] Interviewers: So if the user hasn't planned anything for tomorrow, they will plan it in the calendar, and the notification will read from that. If there's an outfit, it says "You have this outfit." If there isn't, it says "You don't have an outfit planned for tomorrow – choose your items." So overall, we're removing the feature we worked on this week – the one about marking clothes worn today. Do you think that's not needed at all? Or should we rework it?

[09:00.00] Customer: No, specifically that message. I'm removing that window from the frontend entirely.

[09:10.00] Interviewers: Okay.

[09:14.00] Customer: You've already decided everything without me, great.

[09:22.00] Customer: Why is it sending the wrong message? I marked my outfit for today, and it says "You didn't mark your outfit."

[09:30.00] Interviewers: What do you mean?

[09:33.00] Customer: Exactly what I said.

[09:36.00] Interviewers: Where exactly? It doesn't mark it as an outfit for today – it marks it as worn. And in the item card, it shows that you wore it. Or are we talking about different things?

[09:50.00] Customer: I understand what you did. Why are you doing so many unnecessary things?

[09:58.00] Interviewers: We weren't exactly taught to do meaningful things.

[10:05.00] Customer: That's funny. Look – if a user has a specific outfit planned for a specific day, say today, then by default all items in that outfit are marked as worn today. The user doesn't need to separately select what they wore. That's simpler for you and simpler for UX.

[10:25.00] Interviewers: Good. We discussed that. Are we going to discuss statistics?

[10:32.00] Customer: No, not statistics directly. But in the item card, when the user sends it, it appears. In the item card, you can open the app and it shows – if you assembled an outfit yesterday, today it will show that you wore it yesterday. We've already done that. It just says "Last worn" at the bottom of the item card.

[10:52.00] Customer: That's cool.

[10:56.00] Interviewers: Regarding marking when clothes are used – do you have any other concerns? Or maybe something you want to improve or change so we don't do unnecessary things again?

[11:10.00] Customer: No, I don't think there's anything else to add. It's a matter of how you interpret my words.

[11:20.00] Interviewers: Good.

[11:23.00] Customer: I hope you understood.

[11:26.00] Interviewers: Can we write to you about this if needed?

[11:29.00] Customer: Of course.

[19:06.00] Interviewers: Now we need to discuss product readiness for handover. How complete does the product seem to you – would you be able to start using it independently?

[19:25.00] Customer: Finish what we discussed today, and then I think you can start using it independently. When is your course final?

[19:40.00] Interviewers: Next week – July 21st is our presentation.

[19:50.00] Customer: Good.

[19:55.00] Interviewers: Next question – which features already work as you expected?

[20:05.00] Customer: Everything I didn't criticize works as I expected.

[20:15.00] Interviewers: What do you think needs improvement? We just discussed that. Have you already tried using the app in daily life? If yes, how? If not, what's stopping you?

[20:30.00] Customer: One more time – will I use the app?

[20:35.00] Interviewers: Have you already tried using this app in daily life? If yes, tell us how. If not, what's stopping you?

[20:45.00] Customer: No, I'm waiting for you to finish everything.

[20:55.00] Interviewers: The product hasn't been deployed on your side yet – you haven't been given access. What needs to happen on our final week for you to consider the handover complete? Specifically, what do we need to deliver in terms of documentation and files?

[21:15.00] Customer: Two options – either you can export everything as a ZIP file, or you can add Misha to GitHub.

[21:28.00] Interviewers: Good. We have three GitHub repositories. But I think only two are relevant to you – frontend and backend.

[21:42.00] Customer: You decide. Where is the final version of the product stored, fully complete? That's what we need.

[21:55.00] Interviewers: Everything is on the VM that you have access to. Will we still need to do something?

[22:05.00] Customer: Really? Probably not. I'm not sure – better check with Misha.

[22:15.00] Interviewers: Regarding product documentation – explaining how everything works, how we progressed step by step, what we improved – it's in the repository.

[22:28.00] Customer: Great, it's not needed at all.

[22:33.00] Interviewers: Good. Which features or fixes are critical for you in the final version?

[22:45.00] Customer: What I mentioned today. Let's go through the points – how did you understand me?

[22:58.00] Interviewers: So – add a chat with the AI so we can communicate with it, not just view outfits. Move the main screen and the neural network icon in the bottom panel. And change the bot reminder – the outfit planning notification. That's everything for now.

[23:18.00] Customer: And add – if there's no outfit for today, it should be possible to add one from the left panel. Not "no outfit for today," but a button to set an outfit for today or something similar.

[23:35.00] Interviewers: In that window? Yes, good.

[23:40.00] Interviewers: Now, long-term usefulness – how do you think we can ensure the product remains useful after the course ends?

[23:55.00] Customer: Sell it.

[24:00.00] Interviewers: Now we need to do a documentation review. We've prepared several documents that will help you use and potentially extend the product. I've sent you the links. According to the rules of this session, you should open them now and start reading, then give us feedback on what was interesting or useful.

[24:20.00] Customer: I read very fast – I've already read it.

[24:26.00] Interviewers: Where did you have questions or find missing information? What do you think is missing? Anything to add?

[24:38.00] Customer: Who wrote the backend?

[24:42.00] Interviewers: That person isn't here right now.

[24:48.00] Customer: I think it's better to export files as a ZIP. You need to have the API files – repositories won't work because API keys shouldn't be in repositories. You'll need to convert them yourself.

[25:05.00] Interviewers: What if we do two ZIP files?

[25:10.00] Customer: That won't be a problem. If you have API keys in the repository, that's the whole file. Let's check.

[25:22.00] Interviewers: We would have known by now. Notifications come to GitHub immediately, and Docker notifications come to GitHub as well.

[25:38.00] Customer: Why do you have so many Markdown files?

[25:45.00] Interviewers: Unfortunately, one file for each assignment.

[25:52.00] Customer: Seriously?

[25:55.00] Interviewers: Yes – they are very long assignments. Every week all the files are filled out. Some have 20 points, some have 40 sub-points. Up to 42 points in a readme.

[26:12.00] Customer: What's the point?

[26:18.00] Interviewers: That's not for us to say. We wanted to know the point too.

[26:25.00] Customer: I see.

[26:30.00] Interviewers: So, the outcome – readiness for handover. Do you consider it ready, not ready, or partially ready?

[26:42.00] Customer: Partially.

[26:50.00] Interviewers: Good. We received the feedback on what needs to be fixed and what we need to do. We plan to address this in the sprint – maybe within this week. Our plan for the whole week includes monetization, as we discussed, and fixing errors.

[27:10.00] Customer: Do you have anything else?

[27:18.00] Interviewers: No, we're asking – we'll handle monetization and fix errors. We've already sorted out the subscription with you.

[27:32.00] Customer: Anything else for today?

[27:38.00] Interviewers: For today, we have one final question. Do you confirm that after the changes from Week 7, the product will be ready for independent use on your side?

[27:55.00] Customer: What was the beginning of the question?

[28:02.00] Interviewers: Do you confirm that after the changes from Week 7, the product will be ready for independent use on your side?

[28:20.00] Customer: If there are no new changes after your fixes, then yes.

[28:32.00] Interviewers: Good. Thank you very much.

[28:45.00] Customer: Have a great day, everyone.

[28:55.00] Interviewers: Goodbye.

[29:42.00] End of video.

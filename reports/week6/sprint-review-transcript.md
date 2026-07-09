# Interview with customer
**DATE:** 2026-07-09

**Participants:** Evgeniia Zakharova, Veronika Drozd, Ekaterina Kharamanian

-----

[00:00.00] Interviewers: May we record this meeting for internal team review? And if so, may we share an encrypted recording and a web frame?

[00:15.00] Customer: Sure, go ahead.

[00:25.00] Interviewers: Thank you. Today we want to show you the updated version of our application. The goals of this meeting are to demonstrate what's new in the product, discuss whether the product is ready for handover, give you an opportunity to try it, and collect your feedback. For this Sprint Review, we implemented the AI stylist, implemented daily reminders from the bot, fixed the outfit image display error you mentioned last time, and added some documentation. Now we will go through the UAT scenarios.

[00:52.00] Interviewers: Yes, user acceptance tests – as I mentioned, we need to go through them. We need to add an item, delete it, use filters, use the calendar, use the new AI stylist, and then test the reminder functionality.

[customer looks through items in the app]

[01:50.00] Customer: Does it adjust to a specific format?

[01:58.00] Interviewers: No, we haven't had time to implement that yet, and most likely we won't.

[02:08.00] Customer: I think you will. I believe in you.

[customer adds an item to an outfit]

[02:45.00] Customer: How do I make the jacket appear above the pants?

[02:55.00] Interviewers: You need to delete it and add it again.

[03:05.00] Customer: Got it. Why isn't the item loading here?

[03:20.00] Interviewers: We had some issues with capsules – since it's an old one. You'll need to create a new one, because there were problems with the previous version.

[03:50.00] Customer: Why is the AI icon first and the home icon not in the center? It seems more convenient for the user when the main screen is in the middle, not on the left.

[04:10.00] Interviewers: Because the AI stylist is not something users would use every time they open the app. It would be strange to have it in the center. You can tell us if we're wrong – we'll redo it the way you like. But that was the decision we made.

[04:35.00] Customer: Let's look at some social networks or mobile apps. For example, Instagram – we open the homepage, it's on the left. Duolingo – the home icon is on the left. What else? The home icon is on the left everywhere. Why do you think that is?

[05:00.00] Interviewers: If you want, we can move the home icon to the left – it's not difficult to do.

[05:10.00] Customer: It's not about what I like. This is not my personal preference – it's because that's how people process information. We read from left to right, not from the center outward. For people with crossed eyes, maybe the center works, but for normal users, everything goes top to bottom, left to right. It's illogical when you enter the homepage and it's on the far left, and then you can switch to panels on the right. There are standard patterns in apps and SaaS – homepage is always on the left, and the profile is always on the right.

[05:50.00] Interviewers: Okay, we will fix it.

[06:00.00] Customer: How well does it work?

[06:05.00] Interviewers: On a single prompt, as you suggested.

[06:15.00] Customer: How do you communicate with it? Never mind. You've done much more than I expected, of course. How do you interact with it?

[06:30.00] Interviewers: You don't.

[06:35.00] Customer: So you added outfit loading and assembly, but you didn't add a simple chat for communication?

[06:48.00] Interviewers: Why would you need that? To ask questions?

[06:55.00] Customer: Yes, to ask any questions. Then from the chat, you can build functionality on top of it.

[07:10.00] Interviewers: What exactly do you want from it? For it to act as an AI stylist that you can ask about color combinations, outfit assembly, and create outfits from specific items? If we just integrate a neural network, users would interact with it like any other AI – like DeepSeek, for example. I don't think that's what you want.

[07:35.00] Customer: Exactly.

[07:40.00] Interviewers: Oh, that's what you meant? I thought you wanted something narrow and focused.

[07:50.00] Customer: No, actually the opposite – not narrow. I mentioned System Prompt – it's just a configuration on top of the chat, providing context so it responds as an AI stylist. Not just a generic model like DeepSeek, but a stylist who understands color theory, materials, and how to combine them. You went through all this effort but didn't implement the core value. That's funny. But it's cool that the outfit assembly feature works – that's great.

[08:30.00] Interviewers: We'll add it then. Good. Now we need to test the bot. We need to exit the application.

[08:45.00] Customer: The capsule loads in the recycle bin too. Interesting. So where do I need to go?

[08:55.00] Interviewers: To Telegram – the Telegram bot. Let's try sending the link. I've sent it.

[09:05.00] Customer: What do I need to do in the bot?

[09:10.00] Interviewers: You need to check that the bot works.

[customer declined to share Telegram screen]

[09:35.00] Interviewers: Okay, fine. Then we'll take your word for it. In the Telegram bot, open the menu. There are profile settings there. Do you see it?

[09:50.00] Customer: Where? If I press Start, it only offers to open the wardrobe. The menu on the left?

[10:00.00] Interviewers: Yes, the menu on the left. There are profile settings. You can enable or disable notifications and set the time. To demonstrate that notifications work, there's a "Check Now" button in the time setting section. This is specifically for you and for us. You can press "Check Now" and it will send you a notification – the same one that is sent by default at 7 PM.

[10:30.00] Customer: It sends at 7 PM to remind you if you haven't marked the clothes you wore today?

[10:38.00] Interviewers: Yes.

[10:42.00] Customer: But that's for planning clothes – you need to mark what you will wear tomorrow. It's not like calorie tracking where you mark what you ate today – this is forward-looking.

[11:00.00] Interviewers: We do have that function – you can go into the app and mark the outfit you will wear. If it's scheduled, it will automatically count as worn. But if the user doesn't plan an outfit the day before and just wears a t-shirt and shorts, then when the notification arrives, they can mark it so the item is recorded as worn. This is useful because not everyone plans outfits in advance.

[11:30.00] Customer: If there's no outfit for the next day, it sends a reminder to choose an outfit for tomorrow. And if there is an outfit, it sends a morning notification saying "Today you have outfit X."

[11:50.00] Interviewers: Good. What time should the notification be sent? By default, maybe 7 AM or 8 AM? Users can adjust it later, but what should the default be?

[12:05.00] Customer: I'm not sure. Early morning seems a bit off. If it's sent in the evening – if there's an outfit for tomorrow, it says "Tomorrow you have outfit X." If there's no outfit, it says "Choose an outfit for tomorrow."

[12:30.00] Interviewers: So if the user hasn't planned anything for tomorrow, they will plan it in the calendar, and the notification will read from that. If there's an outfit, it says "You have this outfit." If there isn't, it says "You don't have an outfit planned for tomorrow – choose your items." So overall, we're removing the feature we worked on this week – the one about marking clothes worn today. Do you think that's not needed at all? Or should we rework it?

[13:00.00] Customer: No, specifically that message. I'm removing that window from the frontend entirely.

[13:15.00] Interviewers: Okay.

[13:20.00] Customer: You've already decided everything without me, great.

[13:30.00] Customer: Why is it sending the wrong message? I marked my outfit for today, and it says "You didn't mark your outfit."

[13:40.00] Interviewers: What do you mean?

[13:45.00] Customer: Exactly what I said.

[13:50.00] Interviewers: Where exactly? It doesn't mark it as an outfit for today – it marks it as worn. And in the item card, it shows that you wore it. Or are we talking about different things?

[14:10.00] Customer: I understand what you did. Why are you doing so many unnecessary things?

[14:25.00] Interviewers: We weren't exactly taught to do meaningful things.

[14:35.00] Customer: That's funny. Look – if a user has a specific outfit planned for a specific day, say today, then by default all items in that outfit are marked as worn today. The user doesn't need to separately select what they wore. That's simpler for you and simpler for UX.

[15:05.00] Interviewers: Good. We discussed that. Are we going to discuss statistics?

[15:15.00] Customer: No, not statistics directly. But in the item card, when the user sends it, it appears. In the item card, you can open the app and it shows – if you assembled an outfit yesterday, today it will show that you wore it yesterday. We've already done that. It just says "Last worn" at the bottom of the item card.

[15:45.00] Customer: That's cool.

[15:50.00] Interviewers: Regarding marking when clothes are used – do you have any other concerns? Or maybe something you want to improve or change so we don't do unnecessary things again?

[16:10.00] Customer: No, I don't think there's anything else to add. It's a matter of how you interpret my words.

[16:25.00] Interviewers: Good.

[16:30.00] Customer: I hope you understood.

[16:35.00] Interviewers: Can we write to you about this if needed?

[16:40.00] Customer: Of course.

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

[29:38.00] Interviewers: Goodbye.

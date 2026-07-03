# Sprint Review Transcript

**Date:** 2026-07-03
**Participants:** Evgeniia Zakharova, Veronika Drozd, Ekaterina Kharamanian

[00:00.00] Customer: Hi.

[00:15.00] Interviewers: Hello. May we record this session and publish an anonymized transcript in the public GitHub repository? We will remove all personal data.

[00:30.00] Customer: What counts as personal data?

[00:35.00] Interviewers: Your name, and possibly anything else that could identify you personally.

[00:39.00] Customer: Alright, that's fine.

---
## UAT execution

[00:40.00] Interviewers: Thank you. The first part of our interview will be the User Acceptance Test, as we did last time.

[opens Telegram bot]

[01:10.00] Interviewers: This is our Welcome Page.

[01:20.00] Customer: Where can I select the city?

[01:30.00] Interviewers: There is no button to change it. You can try reloading the page – it works for all of us. It might be that your GPS access is blocked. We can help you with that later.

[02:00.00] Customer: Let me check on my phone. On my phone, it doesn't open either.

[02:15.00] Interviewers: It opens for all of us. We can show you this part through our screen. Could you try giving access to your geolocation?

[02:45.00] Customer: No. But even if I give geolocation access, it goes through a third-party service. Other users might have the same problem, and they won't want to search for settings – they won't understand what the issue is.

[03:15.00] Interviewers: In this case, while we were fixing this, we had some issues yesterday and the button disappeared. When you have an address, you can select from a list of cities without going into settings. I'm not sure why it's not showing for you. We will fix it.

[03:45.00] Customer: What are we doing now?

[03:55.00] Interviewers: We need to run the User Acceptance Test. Let's start with the first one – we'll finish with the calendar. We need to add an item, delete it, and check that filtering works. We'll show you the calendar at the end.

[04:15.00] Customer: Can I add outfits here?

[04:20.00] Interviewers: You don't have an outfit for today yet. You can choose one later. First, let's add an item and go through the user tests.

[05:00.00] Customer: Let me find a photo. Oh, it cropped.

[05:15.00] Interviewers: Yes, it cropped. It's just on the background.

[05:25.00] Customer: I was asking about standardization using AI. But that's okay.

[05:35.00] Interviewers: We haven't done that yet. Now, through the "Edit" button, you can delete an item and try searching in the recycle bin to restore it. You can now try that – you restored the item. Now you can use filtering by categories.

[06:10.00] Customer: Where are the filters?

[06:15.00] Interviewers: By filters, we mean you can select category, material, color – click on the triangles, that works as filtering and search. Now let's go to the main screen – the house icon – and check the calendar with the outfit. Click on tomorrow's date. You don't have outfits yet – let's try creating one.

[07:00.00] Customer: So I need to do this first?

[07:05.00] Interviewers: Can you create an outfit? Yes, now? And it's added. For the next day, you can either create an outfit via comment or select an existing one.

[customer creates a capsule]

[09:00.00] Customer: The outfit doesn't save the way I arranged it. And this is a capsule.

[09:10.00] Interviewers: Outfits and capsules are not synced yet – they will be duplicated later. This is still a work in progress. Okay, can I try opening the calendar? Yes, you can create an outfit through the calendar.

[09:30.00] Customer: I'll try both ways. Why did I create a new outfit in the outfits section and it was saved for May 4th? That needs to be fixed. I arranged it differently, and the pants shrank a bit after washing.

[09:55.00] Interviewers: Maybe try through the calendar to complete the UAT test?

[10:00.00] Customer: Yes, now. The outfit arrangement saving needs to be fixed.

[10:15.00] Interviewers: Choose a date – for example, today. Scroll the calendar to July and select a date, otherwise it will be May 13th. Choose July 4th, for example.

[10:30.00] Customer: May 13th, 2027 – it will only appear then. Also, there should be a button here to load an outfit for today directly from this panel, not from somewhere else.

[10:45.00] Interviewers: If there is no outfit, you can add it through the calendar.

[10:50.00] Customer: That's inconvenient.

[10:55.00] Interviewers: Try selecting an outfit for today – July 3rd has a black dot. Choose the outfit you want.

[11:05.00] Customer: Why did it load as items and capsules instead of as an outfit?

[11:15.00] Interviewers: Because the backend is not yet fully implemented the way we want it to be.

[11:30.00] Customer: Okay, fine. A confirmation button is needed – actually, no, it's not needed. It works fine as is.

[11:45.00] Interviewers: Now for the weather. Let us show you how it works – we will fix it today. Let us demonstrate. Can you see it? The idea is that you open the main screen, and it shows your location based on geolocation, and the weather. It works overall. We can change it. There should be a "Change" button – you can set it automatically or select from a list of cities. We will expand the list later. We're not sure which cities to add yet, in case someone doesn't want to share their location. If we want to, we allow it, and it changes – it already works. We can select, for example, Saint Petersburg – now we have the weather for Saint Petersburg.

[14:30.00] Customer: Which API are you using?

[14:35.00] Interviewers: I think it was Openweather – open access, free.

[14:40.00] Customer: Go ahead.

[14:45.00] Interviewers: That's what I asked you about – we haven't changed anything. I asked if we could use it.

[14:50.00] Customer: I don't remember you asking.

[14:55.00] Interviewers: Now, regarding improvements – do you think anything needs to be improved or changed? We understood that outfits should save better, with proper arrangement.

[15:15.00] Customer: Also the AI stylist.

[15:20.00] Interviewers: We mean specifically for the User Acceptance Test you just went through – what would you improve or change?

[15:30.00] Customer: Overall, I like it.

[15:40.00] Interviewers: We will fix the weather issue.

---
## Sprint Review

[18:40.00] Interviewers: Now we move to the second part of our interview – the Sprint Review. During this sprint, our goals were to deliver MVP 2, implementing two user stories: first, weather integration, which you saw, and second, built-in outfit planning with the calendar, which you also saw. We also created architectural documentation – three UML diagrams: Static, Dynamic, and [inaudible]. We linked all technical decisions to quality requirements. The application now shows weather and calendar functionality. We would like to know what else could be improved.

[19:20.00] Customer: For the weather display – it works. For outfit arrangement – it should save the layout. With capsules – you said you'll work on that later. Outfit editing – let me check. I like it, it's fine. Once you fix everything, you can add the stylist and it will be complete. I can't think of anything new right now.

[19:50.00] Interviewers: To conclude the review – there is a risk that the rembg library we use may slow down the CPU due to traffic growth. Our plans for the next sprint are to integrate the AI stylist, as promised, and also implement Telegram bot notifications to remind users if they forgot to add an outfit for today. That is scheduled for next week. Do you have any suggestions for product improvements or things that need to be fixed or added? We will take the feedback into account and adapt the Product Backlog for next week. I think we have already discussed this, so we will proceed accordingly.

[20:30.00] Customer: Thank you, goodbye. Have a good day.

[21:00.00] Interviewers: Goodbye, all the best.

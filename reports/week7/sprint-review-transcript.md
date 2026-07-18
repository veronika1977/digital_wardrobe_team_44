# Interview with customer

[01:21.54] Interviewers: Good afternoon. May we record this meeting for internal team review?

[01:23.00] Customer: Yes.

[01:25.00] Interviewers: Today we want to show you the updated version of our wardrobe application, which is the Final Release Version 3, prepared for this week. The purpose of this meeting is to demonstrate what is new in the product over the past week, review it, and prepare the product for handover for independent use. We also want to give you the opportunity to test key features and collect your feedback. The planned scope for Sprint 5 includes monetization, adding a chat with the AI stylist based on feedback from our previous meeting, and reworking the chatbot to ask users what they will wear tomorrow, also based on feedback. We have completed all tasks and can show you the results. If possible, we can proceed directly to the UAT.

[02:26.25] Customer: It would be easier to show it.

[02:28.00] Interviewers: So you will not be able to conduct the UAT yourself. I can verify it. We just need to go through 7 scenarios: add an item, delete it, test monetization, and use the stylist.

[02:32.00] Customer: All right, let's take a look.

[02:34.00] Interviewers: We will need you to share your screen.

[02:36.00] Customer: Yes, sure.

[difficulties with connection]

----
## UAT tests

[04:20.66] Customer: All right. What exactly do we need to test here?

[04:22.00] Interviewers: We need to add an item, check that filters and search work, delete an item, test the calendar, the stylist, the chat, and the subscription to ensure everything is functional.

[04:28.00] Customer: Good. It would also be helpful to find an image on my laptop.

[04:32.00] Interviewers: We can send you some images so you don't have to search.

[05:25.56] Customer: Please do.

[07:57.03] Interviewers: May I ask – are you sharing your Telegram screen? We need you to share the application.

[08:12.26] Customer: Let me share my screen now. I am here, clicking through.

[08:28.19] Interviewers: We can provide a promo code so you do not need to use a subscription.

[08:46.62] Customer: What does the current setup provide in terms of limits?

[08:51.71] Interviewers: The AI stylist is unavailable without a subscription. Without a subscription, only one capsule, 10 items, and 3 outfits are available. A subscription unlocks everything. We can give you a promo code.

[09:30.08] Customer: Please send the promo code. This is just the recycle bin. I will delete it. I do not want to add more items. It works. Overall, it seems fine.

[10:36.00] Interviewers: Could you go back to the bot and check the commands to receive a notification? There is a menu with three tabs, and profile settings are there. You can set the time and select "right now" to test it. This is specifically for testing. You can also select the 19th, which is tomorrow, to see your outfit for tomorrow.

[10:40.00] Customer: Okay, good.

[11:32.47] Interviewers: Was anything inconvenient or unclear? Is there anything that could be improved?

[11:38.43] Customer: No, I think everything is fine.

-----
## Product readiness discussion
[11:42.45] Interviewers: Now we need to discuss product readiness for handover. How complete does the product seem to you – would you be able to start using it independently?

[11:48.00] Customer: Yes.

[11:50.00] Interviewers: Are there any incomplete parts? Which features already work as you expected?

[11:57.63] Customer: Everything we discussed works as expected.

[12:07.31] Interviewers: Have you already tried using the app in daily life? If not, what is stopping you?

[12:12.00] Customer: Not yet. Nothing is stopping me – I have just been occupied with other tasks. I only saw this bot yesterday when [customer's name] informed me that you would be visiting.

[12:31.72] Interviewers: Is the product deployed on your side?

[12:35.00] Customer: Yes, I provided the VM and have access to it.

[12:38.00] Interviewers: How do you think we can ensure the product remains useful after the course ends?

[12:55.05] Customer: By using it.

[12:59.20] Interviewers: Now we need to review the documentation. I can send you the links to our GitHub.

[14:16.78] Customer: I have reviewed it. The text is clear and well-structured.

[14:20.00] Interviewers: Was anything immediately clear? Were there any questions or missing information?

[14:35.23] Customer: Everything is clear. It is perfect.

[14:40.11] Interviewers: To summarize – the product is ready for handover. We received feedback that everything is sufficient. The final question: do you accept the current document sent as Customer Handover as sufficient for independent use of the product after the tasks completed this week?

[14:45.00] Customer: Yes.

[14:48.00] Interviewers: Good. We will need written confirmation from you. I will send a message in Telegram, and you will need to reply confirming or not confirming.

[14:52.00] Customer: Good.

[14:55.00] Interviewers: One more question regarding project handover. Last week, Mark mentioned we could send ZIP files. Is that necessary if you already have access to the VM?

[15:33.01] Customer: Not particularly. How is everything organized there?

[15:46.80] Interviewers: The frontend bot is in the backend repository, but the structure is somewhat unconventional – both frontend and the Telegram bot are in the root directory. We can send you the specific folder locations. Overall, everything works and is present.

[16:13.22] Customer: I already forked the repository you sent me in the chat.

[16:20.48] Interviewers: However, the frontend and backend versions may not be the latest. Would you prefer us to update the GitHub repository with the latest versions, or should we send ZIP files?

[16:44.50] Customer: ZIP files are not necessary. Since I already forked the repository, you can update it on GitHub. When everything is up to date, just let me know and I will sync it.

[16:59.05] Interviewers: Thank you very much.

[17:01.00] Customer: Thank you as well. Goodbye.

[17:03.00] Interviewers: Goodbye.


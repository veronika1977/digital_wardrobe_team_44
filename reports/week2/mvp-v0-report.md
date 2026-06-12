## Deployment URL for website
[https://agent-6a29aac2b0946--benevolent-frangollo-a08785.netlify.app](https://agent-6a29aac2b0946--benevolent-frangollo-a08785.netlify.app)

## Link on the Telegram mini app  

[https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app](https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)  

## Public video demonstration  

[Video: MVP v0 smoke check](https://drive.google.com/drive/folders/1q9JeW3Yv7yADk_KCXJ51OTBXAKSWv8RX?usp=drive_link)

The video shows:
1. Opening the deployment URL
2. Page loading successfully
3. Clicking on buttons, then alerts appear
4. User can add item
5. Calendar works
6. User can create outfits
7. Bakets work and buttons "Delete" and "Recover" too
8. Filters and searching by item's name work successfully
9. Capsules page works
10. Photo uploading from files sucessfully

# Relationship to prototype and proposed MVP v1 stories

- The Figma prototype demonstrates what the interface should look like  
- MVP v0 is a first small varient of our full MVP
- in MVP v1 we need to add data base to hold information, AI that can remove bacground

## Current limitations, placeholders, and mocks  

- There is no AI that removes bacground  
- There is no backend and data base

## Link to local setup instructions

[Local setup instructions](README.md)

## Repeatable smoke-check scenarios

### Access instructions for the site
1. Open a browser (Chrome, Safari, Firefox)
2. Go to: https://agent-6a29aac2b0946--benevolent-frangollo-a08785.netlify.app

### Steps

#### Steps
1. Verify that the page loads completely without any console or network errors.
2. Check that the application title **"CLOSET FLOW"** is visible on the main screen.
3. Click the **"Add item"** button, fill in the placeholder fields, and submit.
4. Apply any available category filters on the dashboard.
5. Click the **"Create outfit"** button to interact with the outfit/capsule building component.

### Expected result

- The main screen of the application is displayed and functioning
- All buttons are pressed and do their job
- Successful addition and removal of item

### Access instructions for the Telegram Mini App
1. Open a web browser or launch your native Telegram application.
2. Navigate directly to the Mini App link: https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app
3. Confirm the Telegram prompt to launch the built-in web application view.

### Steps

1. Verify that the application initializes successfully inside the Telegram Webview interface.
2. Ensure the branding header **"CLOSET FLOW"** renders perfectly without layout breaking.
3. Interact with the primary action buttons (e.g., tap **"Add item"** or **"Create outfit"**).
4. Test the mock functionality for creating outfits, organizing capsules, or checking the "wear today" state tracking.

### Expected result

- The main screen of the application is displayed and functioning
- All buttons are pressed and do their job
- Successful addition and removal of item

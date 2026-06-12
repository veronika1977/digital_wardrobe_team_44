## Purpose and Description of the MVP v0 Foundation

The MVP v0 delivery for **Closet Flow** establishes a unified, runnable technical foundation.

The core purpose of this baseline is to provide stakeholders and developers with an early, tangible demonstration of how the application will look, feel, and function in its final environment. Instead of implementing complete backend logic or complex processing pipelines, MVP v0 focuses entirely on interface reachability, structural layout validation, and end-to-end deployment verification.

### Key Objectives of the MVP v0 Baseline:
* **Visual and Interactive Framework:** It renders the initial structural layout, typography, and primary branding of "Closet Flow," allowing users to experience the intended design system firsthand.
* **Core Flow & State Exploration:** It implements lightweight client-side state hooks (such as adding/removing mock items, category filtering, and interactive capsule/outfit toggles). This lets anyone interact with the UI to understand the basic navigation, flow, and user journey constraints without crashing the system.
* **Platform Reachability:** It proves that our continuous integration pipeline is functional, demonstrating that the frontend layer successfully initializes both as a standard browser application and as a responsive standalone experience seamlessly wrapped inside the native Telegram Webview wrapper.

Ultimately, MVP v0 serves as a living proof-of-concept that establishes a secure, zero-credential ecosystem, ensuring the team has a reliable and verified pipeline ready for incremental feature development.

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

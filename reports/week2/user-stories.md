# User Stories for Digital Wardrobe

## US-01: Telegram Authentication

**Requirement Status:** Active
**MoSCoW priority:** Must Have

As a new user,  
I want to log in to the app using only my Telegram account without any registration forms,  
so that I can instantly save my wardrobe data and access it from any device where Telegram is installed.

### Notes and constraints
- Data is linked to Telegram ID
- No separate registration required

## US-02: Add Clothing Item with Photo

**Requirement Status:** Active
**MoSCoW priority:** Must Have

As a user,  
I want to upload a photo of my clothing item and input its category and season,  
so that I can start building my digital wardrobe.

### Notes and constraints
- Categories: top, bottom, shoes, accessories
- Seasons: summer, winter, spring, autumn and demiseason
- Photo can be uploaded from gallery or camera

## US-03: AI Outfit Generation

**Requirement Status:** Removed
**Previous MoSCoW priority:** Won't Have

As a non-fashion-expert user,  
I want AI to automatically generate outfit combinations based on my wardrobe,  
so that I do not have to spend time thinking about what matches.

**Reason:** The customer does not want using AI for generating outfit.

## US-04: Tags for Clothing Items

**Requirement Status:** Active
**MoSCoW priority:** Should Have

As a user,  
I want to add category and season tags to clothing items,  
so that I can organize them easily.

### Notes and constraints
- Filtering by tags (e.g. material, color) is supported

## US-05: Capsule Wardrobes

**Requirement Status:** Active
**MoSCoW priority:** Should Have

As a user,  
I want to group specific items into capsules (e.g., 5/10, 8/3),  
so that I can manage my wardrobe faster.

### Notes and constraints
- 8/3 = 8 items generate 3 outfits
- 10/5 = 10 items generate 5 outfits
- accessories are not included

## US-06: Edit Clothing Item

**Requirement Status:** Active
**MoSCoW priority:** Should Have

As a user,  
I want to edit the details of a clothing item (category, season, photo),  
so that I can correct mistakes or update information.

### Notes and constraints
- Edit name, category, season, or replace photo

## US-07: AI Material and Season Detection

**Requirement Status:** Active
**MoSCoW priority:** Could Have

As a busy user,  
I want AI to define materials, seasons, and color from my photo,  
so that I can save time.

### Notes and constraints
- Can be replaced with manual input

## US-08: Automatic Background Removal

**Requirement Status:** Active
**MoSCoW priority:** Must Have

As a user,  
I want the app to automatically remove the background from my photos,  
so that my digital wardrobe looks clean and neat.

### Notes and constraints
- Use AI for removing background

## US-09: Social Network

**Requirement Status:** Removed
**Previous MoSCoW priority:** Won't Have

As a social user,  
I want to post my outfits and accept comments as in a social network,  
so that I can share with my followers.

**Reason:** Turns the app into a full social network. Out of scope for MVP.

## US-10: Share Outfit by Link

**Requirement Status:** Active
**MoSCoW priority:** Could Have

As a social user,  
I want to share my outfits with friends by link in the Telegram mini app,  
so that I can match and get feedback.

### Notes and constraints
- Generate a unique shareable link

## Initial proposed MVP v1 scope

For MVP v1, the following "Must Have" stories are proposed:
- US-01: Telegram Authentication
- US-02: Add Clothing Item with Photo
- US-08: Automatic Background Removal

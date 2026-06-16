# User Stories Registry: Digital Wardrobe

This document maintains the list of all User Stories with their stable IDs to ensure traceability.

## Quick Overview

| Stable ID | Title | Priority | Status | GitHub Issue |
| :--- | :--- | :--- | :--- | :--- |
| **US-01** | Telegram Authentication | Must Have | Active | # |
| **US-02** | Add Clothing Item with Photo | Must Have | Active | # |
| **US-03** | AI Outfit Generation | Won't Have | Removed | # |
| **US-04** | Tags for Clothing Items | Should Have | Active | # |
| **US-05** | Capsule Wardrobes | Should Have | Active | # |
| **US-06** | Edit Clothing Item | Should Have | Active | # |
| **US-07** | AI Material and Season Detection | Could Have | Active | # |
| **US-08** | Automatic Background Removal | Must Have | Active | # |
| **US-09** | Social Network | Won't Have | Removed | # |
| **US-10** | Share Outfit by Link | Could Have | Active | # |
| **US-11** | Delete Item (Soft Delete) | Must Have | Active | # |


## Detailed User Stories

### US-01: Telegram Authentication
**Requirement Status:** Active  
**MoSCoW:** Must Have

As a new user,  
I want to log in to the app using only my Telegram account without any registration forms,  
so that I can instantly save my wardrobe data and access it from any device where Telegram is installed.

**Notes and constraints:**
- Data is linked to Telegram ID  
- No separate registration required

**Acceptance criteria:**
Feature: New user authentication
  Scenario: Successful first-time login and onboarding
    Given I am a new user with a valid Telegram account
    When I open the "Digital wardrobe" Telegram mini-app
    Then I should see the first welcome page
    When I click "Further" on all onboarding pages
    Then I should be redirected to the Home page 
    And I should see an empty wardrobe screen with an "Add a first item" button

### US-02: Add Clothing Item with Photo
**Requirement Status:** Active  
**MoSCoW:** Must Have

As a user,  
I want to upload a photo of my clothing item and input its category and season,  
so that I can start building my digital wardrobe.

**Notes and constraints:**
- Categories: top, bottom, shoes, accessories  
- Seasons: summer, winter, spring, autumn, demiseason  
- Photo can be uploaded from gallery or camera  

**Acceptance criteria:**
Feature: Add clothing item
  Scenario: Successfully adding a new clothing item with required details
    Given I am on the "Add Item" screen
    When I upload a photo from my gallery or camera
    And I select a valid category (e.g., top, bottom) and season (e.g., summer)
    And I click the "Save" button
    Then the item is saved to my digital wardrobe
    And I am redirected to the wardrobe list where the new item is visible
  Scenario: Attempting to save an item with missing required fields
    Given I am on the "Add Item" screen
    When I upload a photo but leave the category or season empty
    And I click the "Save" button
    Then the item is not saved
    And I see a validation error message prompting me to fill in the missing fields

### US-03: AI Outfit Generation
**Requirement Status:** Removed  
**MoSCoW:** Won't Have

As a non-fashion-expert user,  
I want AI to automatically generate outfit combinations based on my wardrobe,  
so that I do not have to spend time thinking about what matches.

**Notes and constraints:**
- Reason for removal: The customer explicitly stated they do not want to use AI for generating outfits.

### US-04: Tags for Clothing Items
**Requirement Status:** Active  
**MoSCoW:** Should Have

As a user,  
I want to add category and season tags to clothing items,  
so that I can organize them easily.

**Notes and constraints:**
- Filtering by tags (e.g., material, color) is supported.

**Acceptance criteria:**
Feature: Tagging and filtering clothing items
  Scenario: Filtering wardrobe by assigned tags
    Given I have clothing items with assigned tags (e.g., material: cotton, color: blue)
    When I apply a filter for a specific tag in the search view
    Then only the clothing items matching the selected tag are displayed

### US-05: Capsule Wardrobes
**Requirement Status:** Active  
**MoSCoW:** Should Have

As a user,  
I want to group specific items into capsules (e.g., 5/10, 8/3),  
so that I can manage my wardrobe faster.

**Notes and constraints:**
- 8/3 = 8 items generate 3 outfits  
- 10/5 = 10 items generate 5 outfits  
- Accessories are not included in the count.

**Acceptance criteria:**
Feature: Capsule wardrobe creation
  Scenario: Successfully creating an 8/3 capsule wardrobe
    Given I have at least 8 clothing items in my wardrobe (excluding accessories)
    When I select exactly 8 items and choose the "8/3" capsule option
    And I confirm the creation
    Then a new capsule is saved
    And it displays the 8 selected items and generates 3 outfit combinations

### US-06: Edit Clothing Item
**Requirement Status:** Active  
**MoSCoW:** Should Have

As a user,  
I want to edit the details of a clothing item (category, season, photo),  
so that I can correct mistakes or update information.

**Notes and constraints:**
- Edit name, category, season, or replace photo.

**Acceptance criteria:**
Feature: Edit clothing item details
  Scenario: Successfully updating clothing item details
    Given I have an existing clothing item in my wardrobe
    When I open the item details and change its category, season, or replace the photo
    And I click "Save"
    Then the item's information is updated in the database
    And the wardrobe list reflects the new details immediately

### US-07: AI Material and Season Detection
**Requirement Status:** Active  
**MoSCoW:** Could Have

As a busy user,  
I want AI to define materials, seasons, and color from my photo,  
so that I can save time.

**Notes and constraints:**
- Can be replaced with manual input if AI fails.

**Acceptance criteria:**
Feature: AI auto-detection of item attributes
  Scenario: AI successfully detects attributes from a photo
    Given I am adding a new clothing item and upload a clear photo
    When the AI detection process is triggered
    Then the material, season, and color fields are automatically populated
    And I can manually edit these fields if the detection is incorrect

### US-08: Automatic Background Removal
**Requirement Status:** Active  
**MoSCoW:** Must Have

As a user,  
I want the app to automatically remove the background from my photos,  
so that my digital wardrobe looks clean and neat.

**Notes and constraints:**
- Use AI for removing background.

**Acceptance criteria:**
Feature: Automatic background removal for clothing photos
  Scenario: Background is successfully removed upon saving
    Given I upload a photo of a clothing item that has a visible background
    When I proceed to save the item
    Then the system processes the image using AI
    And the saved photo displays the clothing item with a transparent or clean solid-color background

### US-09: Social Network
**Requirement Status:** Removed  
**MoSCoW:** Won't Have

As a social user,  
I want to post my outfits and accept comments as in a social network,  
so that I can share with my followers.

**Notes and constraints:**
- Reason for removal: Turns the app into a full social network. Out of scope for MVP.

### US-10: Share Outfit by Link
**Requirement Status:** Active  
**MoSCoW:** Could Have

As a social user,  
I want to share my outfits with friends by link in the Telegram mini app,  
so that I can match and get feedback.

**Notes and constraints:**
- Generate a unique shareable link.

**Acceptance criteria:**
Feature: Share outfit via link
  Scenario: Generating and copying a shareable outfit link
    Given I have created and saved an outfit in the app
    When I click the "Share" button for this outfit
    Then a unique Telegram Mini App link is generated
    And the link is automatically copied to my clipboard for sharing

### US-11: Delete Item (Soft Delete with 14-day Retention)
**Requirement Status:** Active  
**MoSCoW:** Must Have

As a user,  
I want to move deleted clothing items to a "Trash" basket for 14 days before permanent deletion,  
so that I can easily recover accidentally deleted items and keep my active wardrobe view clean.

**Notes and constraints:**
- Deleted items are moved to a separate "Trash" view, not permanently deleted immediately.
- Items remain in the Trash for exactly 14 days.
- After 14 days, the system automatically permanently deletes the item and its photo.
- Users can manually restore items from the Trash before the 14-day period expires.

**Acceptance criteria:**

Feature: Soft delete and trash management
  Scenario: Moving an item to the Trash basket
    Given I have a clothing item in my active wardrobe
    When I select the item and click the "Delete" button
    Then the item is removed from the active wardrobe view
    And the item appears in the "Trash" basket with a deletion timestamp

  Scenario: Permanent deletion after 14 days
    Given an item has been in the "Trash" basket for 14 days
    When the system runs its daily cleanup job
    Then the item and its associated photo are permanently deleted from the database

  Scenario: Restoring an item from the Trash
    Given an item is in the "Trash" basket and has been there for less than 14 days
    When I select the item and click the "Restore" button
    Then the item is removed from the "Trash" basket
    And the item reappears in my active wardrobe view

---

## Initial proposed MVP v1 scope
For MVP v1, the following "Must Have" stories are proposed:  
- US-01: Telegram Authentication  
- US-02: Add Clothing Item with Photo  
- US-08: Automatic Background Removal  
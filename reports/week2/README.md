# Digital Wardrobe

Digital wardrobe Telegram Mini App

## User Stories

All user stories are documented in [user-stories.md](user-stories.md).

### Transcription
The interview's transcription is located in [customer-meeting-transcript.md](customer-meeting-transcript.md).

### Summary

US-01 - Telegram Authentication - Must Have - Active  
US-02 - Add Clothing Item with Photo - Must Have - Active   
US-08 - Automatic Background Removal - Must Have - Active  
US-04 - Tags for Clothing Items - Should Have - Active  
US-05 - Capsule Wardrobes - Should Have - Active  
US-06 - Edit Clothing Item - Should Have - Active   
US-07 -  AI Material Detection - Could Have - Active   
US-10 - Share Outfit by Link - Could Have - Active  
US-03 - AI Outfit Generation - Won't Have - Removed  
US-09  - Social Network - Won't Have - Removed  

**Initial proposed MVP v1 scope:** US-01, US-02, US-08

## Product Interface (Prototype)

**Tool:** Figma  
**Type:** Interactive prototype (Telegram Mini App)

- [Figma Prototype](https://www.figma.com/proto/ZebtG7N3wFGWCVGGdLh6my/Untitled?node-id=2-14&p=f&t=H7sWLnPru4sqBrIr-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1)

### Screens included:
- Main screen with empty wardrobe
- Screen with the process of adding item
- Screen with added item
- All additional pages: basket, calendar, outfits, capsuleas

### Covered user stories:
- US-01 - the user immediately gets into the application
- US-02 - the prototype partially shows the adition of a new item 
- US-04 - the user can choose category, season of a new clothes
- US-05 - there is page with capsules

## MVP v0

No local setup is required  
- [MVP v0 Report](mvp-v0-report.md)
- [Deployed URL](https://agent-6a29aac2b0946--benevolent-frangollo-a08785.netlify.app)
-[Link on Telegram app](https://t.me/digital_wardrobe_app_bot/digital_wardrobe_app)
- [Video Demonstration](https://drive.google.com/drive/folders/1q9JeW3Yv7yADk_KCXJ51OTBXAKSWv8RX?usp=drive_link)


## Local Setup

### Prerequisites
- Node.js 18+
- npm or bun

### Clone and run the frontend

```bash
# Clone the frontend repository
git clone https://github.com/veronika1977/digital_wardrobe_777.git
cd digital_wardrobe_777

# Install dependencies

npm install

# Start development server

npm run dev
```
The frontend of app  will be available at http://localhost:5173


## Links

- [Week 2 Report](README.md)
- [MVP v0 Report](mvp-v0-report.md)
- [User Stories](user-stories.md)
- [Frontend Repository](https://github.com/veronika1977/digital_wardrobe_777)
- [License](../../LICENSE)

## License

This project is licensed under the [MIT License](LICENSE)

## Lychee Link Checker

- **CI Configuration:** [.github/workflows/lychee.yml](../../.github/workflows/lychee.yml)
- **Latest successful run:** [GitHub Actions](https://github.com/veronika1977/digital_wardrobe_team_44/actions/workflows/lychee.yml)

### Excluded Links and Justification  

`http://localhost:5173` - Local development server; not accessible from GitHub   
`https://www.linkedin.com/*` - Requires authentication; blocks automated checkersManual check passed  
`https://github.com/veronika1977/digital_wardrobe_team_44/.*`- Internal repository links  

## Screenshots

### Branch Protection Settings
![Branch protection settings](images/branch-protection-1.png)
![Branch protection settings](images/branch-protection-2.png)
![Branch protection settings](images/branch-protection-3.png)

### Example Reviewed PR
![Example Reviewed PR](images/example_reviewed_PR_1.png)
![Example Reviewed PR](images/example_reviewed_PR_2.png)

### Prototype
![Prototype](images/prototype.png)

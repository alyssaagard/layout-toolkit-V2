# Layout Toolkit

A free, open-source word processing add-in that brings desktop publishing features to your documents. Create brochures, newsletters, event programs, business cards, and flyers with professional templates, brand customization, and built-in folding guides.

Built as an open-source alternative for desktop publishing workflows in word processors.

> **Recommended for desktop and local use.** Layout Toolkit is designed and optimized for the Microsoft Word desktop application on Windows and Mac. While it also works in Word for web (office.com), the full feature set, including precise page setup, print-ready layouts, and PDF export, performs best in the desktop environment.

## Features

**Template Gallery** - Six ready-to-use layouts: tri-fold brochure, bi-fold brochure, classic newsletter, event program, business card, and event flyer. Each generates a complete Word document with placeholder content, formatted with your brand settings.

**Layout Tools** - Direct control over page orientation, paper size, columns (1-4 with configurable gutter spacing), margins, and insertable elements including text placeholders, horizontal dividers, pull quotes, and sidebar callout boxes.

**Brand Profiles** - Save and switch between organization-specific color schemes and font pairings. Brand settings are applied automatically when generating any template.

**Folding and Print Guide** - Built-in visual diagrams showing how to fold tri-fold and bi-fold brochures, along with paper selection and printing tips.

## Installation

### Prerequisites

- Microsoft Word desktop application (Windows or Mac, Microsoft 365 or Office 2021+)
- For development: Node.js 18+

### Desktop Installation (Recommended)

#### Windows

1. Open Word and create a new document.
2. Click **Insert** in the ribbon.
3. Click **My Add-ins** (or **Get Add-ins**, then **My Add-ins** tab).
4. Click **Upload My Add-in**.
5. Browse to `manifest.xml` and click **Upload**.
6. The "Open Toolkit" button will appear on the Home tab.

#### Mac

1. Open Finder. Press **Shift + Cmd + G** and go to:
   ```
   ~/Library/Containers/com.microsoft.Word/Data/Documents/wef
   ```
   If the `wef` folder does not exist, create it:
   ```bash
   mkdir -p ~/Library/Containers/com.microsoft.Word/Data/Documents/wef
   ```
2. Copy `manifest.xml` into that folder:
   ```bash
   cp /path/to/layout-toolkit/manifest.xml ~/Library/Containers/com.microsoft.Word/Data/Documents/wef/
   ```
3. Quit Word completely (Cmd + Q) and reopen it.
4. The "Open Toolkit" button will appear on the Home tab, or check **Insert > Add-ins**.

### Word for Web (Alternative)

Layout Toolkit also works on Word for web at office.com:

1. Open Word at office.com and create a new document.
2. Click **Insert** > **Add-ins** > **Upload My Add-in**.
3. Browse to `manifest.xml` and upload.

Note: Some features such as custom page dimensions and PDF export depend on the desktop application.

### Organizational Deployment

IT administrators can deploy the add-in to all users via the **Microsoft 365 admin center** under Settings > Integrated Apps. This eliminates the need for individual sideloading.

## Development

```bash
git clone https://github.com/alyssaagard/layout-toolkit-V2.git
cd layout-toolkit-V2
npm install
npm run dev
```

This starts a local HTTPS development server on port 3000.

For a production build:

```bash
npm run build
```

The `dist/` folder can be deployed to any static host. The `docs/` folder is configured for GitHub Pages.

## Project Structure

```
layout-toolkit-V2/
├── manifest.xml                    # Office Add-in manifest
├── package.json                    # Dependencies and scripts
├── webpack.config.js               # Build configuration
├── assets/                         # Source icons
├── docs/                           # GitHub Pages deployment (production build)
├── dist/                           # Production build output
├── src/
│   ├── taskpane/
│   │   ├── taskpane.html           # UI: 4-tab layout (Templates, Layout, Branding, Guide)
│   │   ├── taskpane.css            # Stylesheet
│   │   └── taskpane.js             # Controller: Office init, events, template orchestration
│   ├── templates/
│   │   └── templateDefinitions.js  # Template metadata, SVG thumbnails, Word JS API builders
│   └── helpers/
│       └── utils.js                # Brand storage, status messaging, document helpers
├── LICENSE                         # MIT License
└── README.md
```

## Compatibility

| Platform | Status | Notes |
|---|---|---|
| Word for Windows (Microsoft 365) | Recommended | Full feature support |
| Word for Mac (Microsoft 365) | Recommended | Full feature support |
| Word for Windows (Office 2021) | Supported | Full feature support |
| Word for Web (office.com) | Supported | Some features limited |
| Word for iPad | Partial | Task pane add-ins supported |

## Licensing

This project is licensed under the MIT License. No special license from Microsoft is required to create, distribute, or use a Word Add-in. Office.js is loaded from Microsoft's public CDN at no cost.

## Contributing

Contributions welcome. Please open an issue before submitting a pull request for major changes.

Areas where help is especially useful:
- Additional templates (booklets, certificates, letterheads, postcards)
- Accessibility improvements
- Localization / internationalization
- Testing across platforms
- A Google Docs (Apps Script) port

## Author

Developed by Alyssa I. Agard.

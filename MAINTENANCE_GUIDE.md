# Website Maintenance Guide
**Vivian Ku Personal Website**

This guide will help you maintain, update, and customize your personal website. No prior coding experience required—just follow these step-by-step instructions.

---

## Table of Contents
1. [Site Overview](#site-overview)
2. [Common Updates](#common-updates)
3. [Updating Digital Vivian Chatbot](#updating-digital-vivian-chatbot)
4. [Adding New Content](#adding-new-content)
5. [Customizing Design](#customizing-design)
6. [Publishing Changes](#publishing-changes)
7. [Troubleshooting](#troubleshooting)

---

## Site Overview

Your website is a single HTML file (`index.html`) that contains:
- **HTML**: The structure and content (what you see)
- **CSS**: The styling (how it looks)
- **JavaScript**: The interactivity (how it behaves)

**Key Sections:**
- Hero (your name and tagline)
- About Me (bio, mission, and sidebar pillars)
- What I Do (your services)
- Selected Writing (featured articles)
- Let's Connect (contact)
- Footer (social links)
- Digital Vivian (AI chatbot)

---

## Common Updates

### 1. Updating Your Bio

**Location:** Lines ~1021-1062

**Steps:**
1. Open `index.html` in a text editor (VS Code, Sublime, or even TextEdit)
2. Find the `<section id="about">` section
3. Update the paragraph text between `<p>` and `</p>` tags
4. Save the file

**Example:**
```html
<p>
    I'm an AI Strategist and Product Manager, specialising in building AI-driven products for
    asset-intensive industries such as smart cities, energy, and manufacturing.
</p>
```

### 2. Adding a New Article

**Location:** Lines ~1135-1175 (Writing section)

**Steps:**
1. Find the `<ul class="writing-list">` section
2. Copy an existing `<li class="writing-item">` block
3. Paste it above the closing `</ul>` tag
4. Update:
   - `href=`: Your article URL
   - `<span class="writing-category">`: Category (Strategy, Infrastructure, etc.)
   - `<div class="writing-title">`: Article title
   - `<div class="writing-meta">`: Article description

**Example:**
```html
<li class="writing-item">
    <a href="YOUR_ARTICLE_URL" target="_blank" rel="noopener noreferrer">
        <span class="writing-category">Strategy</span>
        <div class="writing-title">Your New Article Title</div>
        <div class="writing-meta">A brief description of your article.</div>
    </a>
</li>
```

### 3. Updating Contact Email

**Location:** Line ~1186

**Steps:**
1. Find `mailto:vivian.ku.future@gmail.com`
2. Replace with your new email address
3. Update the displayed text as well

### 4. Updating the "Based In" Location

**Location:** Lines ~1077-1080

**Steps:**
1. Find `<span class="pillar-label">Based In</span>`
2. Update the text in `<div class="pillar-text">` below it
3. Update the `data-zh` attribute for Chinese translation if needed

**Example:**
```html
<div class="pillar-text" data-zh="新城市 / 台灣">New City, UK / Taiwan</div>
```

### 5. Adding a New Leadership Role

**Location:** Lines ~1070-1076

**Steps:**
1. Find the "Leadership & Community" pillar
2. Add a new `<p>` tag inside the `<div class="pillar-text">` section

**Example:**
```html
<div class="pillar-text">
    <p>AI <span class="amp">&</span> Data Meetup @ London (Organiser)</p>
    <p>Tech London Advocate — Taiwan Working Group (Volunteer)</p>
    <p>YOUR NEW ROLE HERE</p>
</div>
```

---

## Updating Digital Vivian Chatbot

### 1. Changing the Greeting Message

**Location:** Line ~1335

**Steps:**
1. Find `const chatData = {`
2. Locate the `start:` section
3. Update the `message:` text

**Example:**
```javascript
start: {
    message: "Welcome! I'd love to tell you about my work...",
    options: [
        // ... options here
    ]
},
```

### 2. Adding a New Topic

**Steps:**
1. Add a new option to the `start` section
2. Create a new response object below

**Example:**
```javascript
// In start section:
options: [
    { text: "What drives your work?", step: "principles" },
    { text: "My new topic", step: "newtopic" },  // NEW
    // ... other options
]

// Below, add:
newtopic: {
    message: "Here's information about the new topic...",
    options: [
        { text: "Read more", url: "https://example.com" },
        { text: "Something else?", step: "start" }
    ]
},
```

### 3. Updating an Existing Response

**Location:** Lines ~1346-1385

**Steps:**
1. Find the response step you want to update (e.g., `principles:`, `strategy:`)
2. Update the `message:` text
3. Add or remove options as needed

**Example:**
```javascript
principles: {
    message: "Updated message about my principles...",
    options: [
        { text: "Tell me more about Strategy", step: "strategy" },
        { text: "Something else?", step: "start" }
    ]
},
```

### 4. Adding a Link to External Content

**Steps:**
1. Add an option with `url:` instead of `step:`
2. The link will open in a new tab

**Example:**
```javascript
options: [
    { text: "Read my article", url: "https://medium.com/@vivian-ku/article" },
    { text: "Something else?", step: "start" }
]
```

---

## Adding New Content

### 1. Adding a New Service Card

**Location:** Lines ~1086-1121 (What I Do section)

**Steps:**
1. Copy an existing `<div class="card">` block
2. Paste it before the closing `</div>` of `cards-grid`
3. Update the content:
   - `<h3>`: Service title
   - `<p>`: Service description
   - `<li>`: Bullet points

**Example:**
```html
<div class="card">
    <h3>New Service Name</h3>
    <p>Description of what you offer...</p>
    <ul>
        <li>Key point 1</li>
        <li>Key point 2</li>
        <li>Key point 3</li>
    </ul>
</div>
```

### 2. Adding a New Social Media Link

**Location:** Lines ~1205-1233 (Footer)

**Steps:**
1. Find the `<nav class="contact-links">` section
2. Copy an existing `<a>` block with SVG
3. Update the `href` and `aria-label`
4. Replace the SVG code (find SVG icons at [heroicons.com](https://heroicons.com))

---

## Customizing Design

### 1. Changing Colors

**Location:** Lines ~37-44 (CSS Variables)

**Steps:**
1. Find the `:root` section at the top of the `<style>` tag
2. Update the color values

**Current colors:**
```css
:root {
    --text-primary: #1a1a1a;       /* Main text color */
    --text-secondary: #4a4a4a;     /* Secondary text */
    --accent-color: #5d7465;       /* Links and accents */
    --accent-terracotta: #b47b5e;  /* Warm accent */
    --border-color: #e5e5e5;       /* Borders */
}
```

**Tips:**
- Use hex codes (#1a1a1a) or rgba values
- Test changes to ensure readability
- Keep contrast high for accessibility

### 2. Changing Fonts

**Location:** Lines ~28-35

**Steps:**
1. Find `@import url` for Google Fonts
2. To use a different font:
   - Go to [fonts.google.com](https://fonts.google.com)
   - Select your font
   - Copy the import code
   - Replace the existing `@import`
   - Update `--font-main` or `--font-headings`

**Example:**
```css
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;700&display=swap');

:root {
    --font-main: 'Outfit', sans-serif;
}
```

### 3. Adjusting Spacing

**Common spacing locations:**
- Section margins: `section { margin-bottom: 6rem; }` (Line ~194)
- Header padding: `header { padding: 4rem 2rem; }` (Line ~209)
- Card grid gap: `.cards-grid { gap: 2rem; }` (Line ~814)

**Tips:**
- `rem` units: 1rem = 16px (typically)
- Increase for more space, decrease for less
- Keep proportions consistent

---

## Publishing Changes

### Option 1: GitHub Pages (Recommended)

**Initial Setup:**
1. Create a GitHub account (if you don't have one)
2. Create a new repository named `yourusername.github.io`
3. Upload `index.html` and the `asset` folder
4. Go to Settings → Pages
5. Select main branch as source
6. Your site will be live at `https://yourusername.github.io`

**Updating:**
1. Edit `index.html` locally
2. Commit and push changes to GitHub
3. Changes go live automatically in ~1-2 minutes

### Option 2: Custom Domain

**If you have a domain:**
1. In your GitHub repo settings, add your custom domain
2. Update DNS records at your domain provider:
   - Add a CNAME record pointing to `yourusername.github.io`
3. Enable HTTPS in GitHub Pages settings

### Option 3: Other Hosting

Upload `index.html` and the `asset` folder to:
- **Netlify**: Drag and drop deployment
- **Vercel**: Connect to GitHub for auto-deploy
- **Traditional hosting**: Use FTP/SFTP to upload files

---

## Troubleshooting

### Issue: Changes don't appear on the site

**Solutions:**
1. **Hard refresh:** Cmd+Shift+R (Mac) or Ctrl+Shift+R (Windows)
2. **Clear cache:** Browser settings → Clear browsing data
3. **Check file saved:** Ensure you saved `index.html` after editing
4. **Verify upload:** Confirm the updated file was uploaded to your host

### Issue: Chatbot not working

**Common causes:**
1. **JavaScript error:** Check browser console (F12 → Console tab)
2. **Missing comma:** Ensure commas between chat options
3. **Syntax error:** Verify quotes match (opening " matches closing ")

**How to debug:**
1. Open browser DevTools (F12)
2. Check Console for red error messages
3. Error will show line number

### Issue: Layout broken on mobile

**Solutions:**
1. Check responsive CSS (lines with `@media`)
2. Test in browser DevTools Device Mode (Cmd+Shift+M)
3. Ensure all closing tags match opening tags

### Issue: Images not loading

**Solutions:**
1. Verify image path is correct
2. Check file names match exactly (case-sensitive)
3. Ensure images are in the `asset` folder
4. Use relative paths: `asset/filename.jpg`

---

## Best Practices

### Before Making Changes
1. **Back up your file:** Save a copy of `index.html` before editing
2. **Test locally:** Open the file in a browser before uploading
3. **Use version control:** GitHub keeps a history of all changes

### When Editing Code
1. **Maintain indentation:** Keep code organized and readable
2. **Don't delete closing tags:** Every `<div>` needs a `</div>`
3. **Test incrementally:** Make small changes and test often
4. **Comment your changes:** Add `<!-- Notes -->` for future reference

### Content Updates
1. **Keep it concise:** Shorter paragraphs are more readable
2. **Update regularly:** Add new articles and projects
3. **Check links:** Ensure all URLs work and open correctly
4. **Proofread:** Check spelling and grammar

### Performance
1. **Optimize images:** Compress before uploading (use TinyPNG)
2. **Minimize code:** Remove unused CSS/JavaScript (advanced)
3. **Test speed:** Use PageSpeed Insights

---

## Quick Reference

### File Structure
```
vivianku/
├── index.html          (Your website - edit this!)
├── asset/              (Images folder)
│   └── portrait_placeholder.jpg
└── note.md            (Your notes)
```

### Common Line Numbers
- **Hero section:** ~988-1042
- **About Me:** ~1045-1084
- **What I Do:** ~1087-1122
- **Writing:** ~1125-1176
- **Contact:** ~1178-1195
- **Footer:** ~1198-1233
- **Digital Vivian:** ~1333-1388
- **CSS Styles:** ~27-951
- **JavaScript:** ~1267-1453

### Getting Help
1. **Browser DevTools:** F12 or Cmd+Option+I
2. **W3Schools:** [w3schools.com](https://w3schools.com) for HTML/CSS reference
3. **Stack Overflow:** Search for specific error messages
4. **MDN Web Docs:** [developer.mozilla.org](https://developer.mozilla.org) for detailed reference

---

## Next Steps

Now that you have this guide, try making a small change:
1. Update your bio with a new achievement
2. Add a recent article to your writing section
3. Test locally by opening `index.html` in your browser
4. If it looks good, publish the changes!

Remember: Start small, test often, and don't be afraid to experiment. You can always revert to a previous version if needed.

**Questions?** Review this guide and use browser DevTools to understand what's happening. The more you practice, the more comfortable you'll become with maintaining your site.

---

*Last updated: January 2026*

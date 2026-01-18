# Website Maintenance Guide
**Vivian Ku Personal Website (Jekyll Edition)**

This guide helps you maintain your bilingual website. The site now uses **Jekyll** to manage English and Chinese content efficiently.

---

## Table of Contents
1. [Site Overview](#site-overview)
2. [Managing Bilingual Content](#managing-bilingual-content)
3. [Language Toggle Settings](#language-toggle-settings)
4. [Updating Digital Vivian Chatbot](#updating-digital-vivian-chatbot)
5. [Customizing Design](#customizing-design)
6. [Publishing Changes](#publishing-changes)
7. [Troubleshooting](#troubleshooting)

---

## Site Overview

Your website is a system that builds pages for you:

*   **`admin/`**: **THE CMS lives here.** (Access `/admin` on your site to edit content visually).
*   **`_writing/`**: **BLOG POSTS live here.** Each article is a separate file.
*   **`_data/content.yml`**: **GLOBAL TEXT lives here.** (Navigation, Hero, About me, Services).
*   **`_layouts/default.html`**: **THE DESIGN lives here.**

---

## Managing Content with Decap CMS

**CMS URL:** `https://your-username.github.io/vivianku/admin`

The best way to manage your site is through the **Decap CMS** interface. However, because your site is hosted on GitHub Pages, you need to enable the "Login" backend first.

### 0. Initial Setup (One-time only)

To allow logging in to your `/admin` page, we use **Netlify Identity** (Free).

1.  **Sign up for Netlify:** Go to [netlify.com](https://www.netlify.com/) and sign up with your GitHub account.
2.  **New Site from Git:** Click "Add new site" -> "Import an existing project" -> "GitHub".
3.  **Select Repository:** Choose your `vivianku` repository.
4.  **Deploy:** Click "Deploy" (Using the default settings is fine, we mainly need the key feature).
5.  **Enable Identity:**
    *   Go to **Site Settings** -> **Identity**.
    *   Click **Enable Identity**.
    *   Under **Registration preferences**, select **Invite only** (so random people can't sign up).
    *   Under **Services** -> **Git Gateway**, click **Enable Git Gateway**.
6.  **Invite Yourself:**
    *   Go to the **Identity** tab at the top.
    *   Click **Invite users** and enter your email.
    *   Check your email and click the confirmation link.

**IMPORTANT:** Once this is set up, you can go to `your-site-url/admin` and log in!

### 1. Adding a New Writing Piece
1.  Log in to the `/admin` dashboard.
2.  Click **Selected Writing** -> **New Selected Writing**.
3.  Fill in the English and Chinese fields.
4.  Click **Publish** -> **Publish now**. 
5.  Wait about 1-2 minutes for your website to update.

### 2. Updating Hero, About, or Services
1.  In the CMS, click **Site Content** -> **Global Content**.
2.  Edit any text (biographies, service descriptions, navigation labels).
3.  Click **Publish**.

---

## Managing Content (The Manual Way)

If you prefer to edit files directly in your code editor:

### 1. Adding a New Article
Create a new `.md` file in `_writing/` (e.g., `my-new-post.md`):

```yaml
---
category: Strategy
title:
  en: "English Title"
  zh: "中文標題"
meta:
  en: "English summary..."
  zh: "中文摘要..."
url: "https://link-to-article.com"
---
```

### 2. Updating Bio or Services
Edit `_data/content.yml`. All text is organized by section with `en` and `zh` keys.

---

## Language Toggle Settings

**Location:** `_layouts/default.html` (Line ~140)

You can enable or disable the "中 / EN" button if you're not ready for the bilingual version yet.

### To Disable (Hide the Button)
Wrap the toggle code in Liquid comments:
```html
    <!-- Language Toggle Link -->
    {% comment %}
    {% if page.lang == "en" %}
    ...
    {% endif %}
    {% endcomment %}
```

### To Enable (Show the Button)
Simply remove the `{% comment %}` and `{% endcomment %}` lines.

---

## Updating Digital Vivian Chatbot

**Location:** `_layouts/default.html` (Scroll to the bottom, `<script>` section ~Line 1340)

The chatbot logic is written in JavaScript.

### 1. Changing Messages
Find the `const chatData` block. Update the text inside `message: "..."`.

```javascript
start: {
    message: "Welcome! Here is my new greeting...",
    options: [...]
}
```

### 2. Adding a New Conversation Step
1.  Add a new option to an existing step: `{ text: "New Topic", step: "newtopic" }`
2.  Create the `newtopic` object:
```javascript
newtopic: {
    message: "Here is the response for the new topic.",
    options: [
        { text: "Back to start", step: "start" }
    ]
},
```

---

## Customizing Design

**Location:** `_layouts/default.html` (CSS section at the top)

### 1. Changing Colors
Find the `:root` variables at the top of the `<style>` block:
```css
:root {
    --text-primary: #1A1A1A;
    --accent-color: #4A5A6A;
    --bg-color: #FDFDFC;
}
```

### 2. Changing Fonts
Find the Google Fonts link in the `<head>` section and the Font Family variables in `:root`.

---

## Publishing Changes

Since you use **GitHub Pages**, deployment is automatic.

1.  **Open Terminal** in your project folder.
2.  **Commit & Push** your changes:
    ```bash
    git add .
    git commit -m "Updated content"
    git push origin main
    ```
3.  **Wait** 1-2 minutes for GitHub to build the site.
4.  **Visit**: [viviankuku.github.io/vivianku/](https://viviankuku.github.io/vivianku/)

---

## Troubleshooting

### "Liquid Exception" / Build Failed
*   **Cause**: Usually a syntax error in `_data/content.yml`.
*   **Fix**: Check your YAML. Did you forget a closing quote? is the indentation lined up perfectly? YAML is very strict about spaces.

### Changes not showing
*   **Fix**: Hard refresh your browser (Cmd+Shift+R). GitHub Pages can take up to 2-3 minutes to update.

### Weird text like "{{ page.lang }}" showing on screen
*   **Cause**: You opened `index.html` directly in Chrome.
*   **Fix**: You must view the **deployed version** on GitHub, or run `jekyll serve` to view it locally. You cannot open the file directly anymore.

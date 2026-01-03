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

Your website is no longer just one file. It is a system that builds pages for you:

*   **`_data/content.yml`**: **ALL TEXT lives here.** (Bio, Articles, Service descriptions).
*   **`_layouts/default.html`**: **THE DESIGN lives here.** (HTML structure, CSS styling, Javascript logic).
*   **`index.html` & `zh/index.html`**: These are just "entry points" that tell the system which language to load. **Do not edit these.**

---

## Managing Bilingual Content

**Location:** `_data/content.yml`

This is the most common task. All text is stored in "blocks" with `en` (English) and `zh` (Chinese) keys.

### 1. Updating Text
Find the section you want to change (e.g., `hero`, `about`) and edit the text inside the quotes.

```yaml
hero:
  role:
    en: "AI Strategy Leader"    <-- English
    zh: "AI 策略負責人"           <-- Chinese
```

### 2. Adding a New Article
Scroll to the `writing: -> items:` section in `_data/content.yml`. Add a new block:

```yaml
  - category: "Strategy"
    title:
      en: "Your New Article Title"
      zh: "新文章標題"
    meta:
      en: "Short description in English."
      zh: "简短的中文描述。"
    url: "https://your-article-link.com"
```

### 3. Adding a New Service
Scroll to the `work: -> cards:` section. Add a new block:

```yaml
    - title:
        en: "New Service"
        zh: "新服務"
      desc:
        en: "Description of what you do."
        zh: "服務描述。"
      items:
        en:
          - "Service Point 1"
          - "Service Point 2"
        zh:
          - "服務重點 1"
          - "服務重點 2"
```

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

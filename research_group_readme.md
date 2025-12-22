# Research Group Website

A clean, minimalist academic research group website built with Jekyll and GitHub Pages.

## 🌐 Live Site

Visit the site at: `https://meincv.github.io/mysmartfarming12`

## 📁 Project Structure

```
/
├── _config.yml                 # Site configuration and settings
├── _layouts/                   # HTML templates for pages
│   └── default.html           # Main layout template
├── _includes/                  # Reusable HTML components (currently empty)
│   └── footer.html            # Footer component (unused)
├── _data/                      # YAML data files for structured content
│   ├── people.yml             # Team members data
│   ├── publications.yml       # Publications metadata
│   └── news.yml               # News items
├── assets/                     # Static files (CSS, images)
│   ├── css/
│   │   └── style.css          # Main stylesheet
│   └── images/
│       ├── header.jpg         # Header landscape image (all pages)
│       └── people/            # Team member photos
│           ├── e.jpeg         # Ehsan's photo
│           ├── f.jpeg         # Florian's photo
│           ├── g.jpeg         # Georg's photo
│           ├── h.jpeg         # Harsha's photo
│           ├── j.jpeg         # Jessica's photo
│           ├── l.jpeg         # Leonie's photo
│           └── m.jpeg         # Marco's photo
├── index.md                    # Homepage
├── people.md                   # Team members page
├── research.md                 # Research overview
├── publications.md             # Publications list
├── teaching.md                 # Teaching information
├── photos.md                   # Photo gallery
├── news.md                     # News and updates
└── positions.md                # Open positions
```

## 🚀 Quick Start

### Local Development

1. **Install Jekyll:**
   ```bash
   gem install bundler jekyll
   ```

2. **Clone the repository:**
   ```bash
   git clone https://github.com/meincv/mysmartfarming12.git
   cd mysmartfarming12
   ```

3. **Run the site locally:**
   ```bash
   jekyll serve
   ```

4. **View in browser:**
   Open `http://localhost:4000/mysmartfarming12/`

### Deployment

The site automatically deploys to GitHub Pages when you push to the main branch. No additional configuration needed!

## 🎨 Customization Guide

### 1. Basic Site Settings

Edit `_config.yml` to change fundamental site information:

```yaml
title: Research Group Name          # Change your group name
email: contact@university.edu       # Contact email
description: Academic research...   # Site description for SEO
url: "https://meincv.github.io"    # Your GitHub Pages URL
baseurl: "/mysmartfarming12"       # Your repository name
```

**After changing `_config.yml`, restart Jekyll server for changes to take effect.**

### 2. Navigation Menu

To add/remove/reorder menu items, edit the `navigation` section in `_config.yml`:

```yaml
navigation:
  - title: Home
    url: /index.html
  - title: New Page        # Add new menu item
    url: /newpage.html
```

**Remember:** Create the corresponding `.md` file (e.g., `newpage.md`) for new menu items.

### 3. Header Image

Replace `/assets/images/header.jpg` with your own image:

- **Recommended size:** 1600x800px (or any 2:1 aspect ratio)
- **Format:** JPG, PNG, or WebP
- **Keep the filename** as `header.jpg` or update `_config.yml`:

```yaml
header_image: /assets/images/your-new-header.jpg
```

## 👥 Managing Team Members

### Adding a New Person

1. **Add photo** to `/assets/images/people/`:
   - Filename: `initial.jpeg` (e.g., `j.jpeg` for John)
   - Recommended size: 200x200px or larger (will be displayed at 80x80px)

2. **Edit** `_data/people.yml` and add to appropriate category:

```yaml
# For a new PhD student:
phd_students:
  - name: John Doe
    role: PhD Student
    photo: /assets/images/people/j.jpeg
    description: "John is a PhD student working on machine learning applications in agriculture."
```

### Available Categories

- `pi` - Principal Investigator
- `postdocs` - Postdoctoral Researchers
- `phd_students` - PhD Students
- `assistants` - Student Assistants

### Adding a New Category

1. **Add to** `_data/people.yml`:
```yaml
# New category for Master's students
masters_students:
  - name: Jane Smith
    role: Master's Student
    photo: /assets/images/people/js.jpeg
    description: "Jane is working on her Master's thesis..."
```

2. **Add section to** `people.md`:
```markdown
### Master's Students

{% for person in site.data.people.masters_students %}
<div class="person-card">
  <img src="{{ person.photo | relative_url }}" alt="{{ person.name }}">
  <div class="person-info">
    <h4>{{ person.name }}</h4>
    <span class="role">{{ person.role }}</span>
    <p>{{ person.description }}</p>
  </div>
</div>
{% endfor %}
```

### Removing a Person

Simply delete their entry from `_data/people.yml`. You can optionally remove their photo from `/assets/images/people/`.

## 📝 Updating Content Pages

Each page is a Markdown (`.md`) file in the root directory. Edit them directly:

### Homepage (`index.md`)

```markdown
---
layout: default
title: Home
---

Welcome to our research group! We focus on...

You can use standard Markdown formatting:
- **Bold text**
- *Italic text*
- [Links](https://example.com)
- ![Images](/assets/images/photo.jpg)
```

### Research Page (`research.md`)

Add research projects, descriptions, and related images:

```markdown
---
layout: default
title: Research
---

## Current Projects

### Project 1: Smart Farming
We are developing AI-powered solutions for...

### Project 2: Precision Agriculture
Our work focuses on...
```

### Publications Page (`publications.md`)

**Option 1: Simple list in Markdown**
```markdown
---
layout: default
title: Publications
---

## 2024

1. Author1, Author2. "Paper Title." *Journal Name*, 2024.
2. Author1, Author2. "Another Paper." *Conference Name*, 2024.

## 2023

1. Previous work...
```

**Option 2: Structured YAML data** (recommended for many publications)

Edit `_data/publications.yml`:
```yaml
publications:
  - year: 2024
    papers:
      - title: "Paper Title Here"
        authors: "Author1, Author2, Author3"
        venue: "Journal of Agriculture Technology"
        link: "https://doi.org/..."
        type: "journal"
      
      - title: "Conference Paper"
        authors: "Author1, Author2"
        venue: "CVPR 2024"
        link: "https://..."
        type: "conference"
```

Then update `publications.md`:
```markdown
---
layout: default
title: Publications
---

{% for pub in site.data.publications.publications %}
## {{ pub.year }}

{% for paper in pub.papers %}
- **{{ paper.title }}**  
  {{ paper.authors }}  
  *{{ paper.venue }}* [Link]({{ paper.link }})
{% endfor %}
{% endfor %}
```

### News Page (`news.md`)

**Simple approach:**
```markdown
---
layout: default
title: News
---

**December 2024:** We received a grant from...

**November 2024:** New paper accepted at...

**October 2024:** Welcome to our new PhD student...
```

**Structured approach using YAML:**

Edit `_data/news.yml`:
```yaml
news_items:
  - date: "2024-12-15"
    title: "Grant Award"
    description: "Our group received funding from..."
  
  - date: "2024-11-20"
    title: "Paper Accepted"
    description: "Our work on X has been accepted to..."
```

Then update `news.md`:
```markdown
---
layout: default
title: News
---

{% for item in site.data.news.news_items %}
**{{ item.date }}:** {{ item.title }}  
{{ item.description }}

{% endfor %}
```

### Photos Page (`photos.md`)

Add image gallery:
```markdown
---
layout: default
title: Photos
---

## Lab Activities

![Lab meeting](/assets/images/gallery/lab-meeting.jpg)
*Monthly lab meeting, December 2024*

![Field work](/assets/images/gallery/fieldwork.jpg)
*Field work in Bavaria*

## Group Events

![Conference](/assets/images/gallery/conference.jpg)
*Presenting at CVPR 2024*
```

### Open Positions (`positions.md`)

```markdown
---
layout: default
title: Open Positions
---

## Current Openings

### PhD Position in Computer Vision
**Start date:** April 2025  
**Requirements:**
- Master's degree in Computer Science or related field
- Experience with deep learning frameworks
- Strong programming skills in Python

**To apply:** Send CV and cover letter to contact@university.edu

---

### Postdoctoral Researcher
**Project:** Smart Agriculture Systems  
**Duration:** 2 years  
**Deadline:** January 31, 2025

[More details and application](https://university.edu/jobs/123)
```

## 🎨 Styling and Design

### Changing Colors

Edit `assets/css/style.css`:

```css
/* Main text color */
body {
    color: #333;  /* Change to your preferred color */
}

/* Headings color */
h2, h3 {
    color: #111;  /* Change heading color */
}

/* Link colors */
nav a {
    color: #666;  /* Default link color */
}

nav a:hover {
    color: #000;  /* Hover color */
}
```

### Changing Fonts

```css
body {
    font-family: "Georgia", serif;  /* Change to preferred font */
}

/* For navigation */
nav a {
    font-family: "Helvetica", "Arial", sans-serif;
}
```

### Adjusting Layout Width

```css
/* Change max-width from 800px to your preference */
header, main, footer {
    max-width: 1000px;  /* Wider layout */
}
```

### Person Photo Style

Change from circular to square:
```css
.person-card img {
    border-radius: 4px;  /* Square with rounded corners */
    /* or border-radius: 0; for sharp corners */
}
```

## 📸 Image Guidelines

### Header Image
- **Dimensions:** 1600x800px (2:1 ratio recommended)
- **File size:** Under 500KB for fast loading
- **Format:** JPG (for photos) or PNG (for graphics)
- **Location:** `/assets/images/header.jpg`

### People Photos
- **Dimensions:** 200x200px minimum
- **Display size:** 80x80px (automatically resized)
- **Format:** JPEG or PNG
- **Style:** Professional headshots work best
- **Location:** `/assets/images/people/`

### General Images
- **Optimize** images before uploading (use tools like TinyPNG)
- **Naming:** Use lowercase with hyphens (e.g., `lab-meeting-2024.jpg`)
- **Alt text:** Always provide descriptive alt text for accessibility

## 🔧 Advanced Customization

### Adding a Blog Section

1. **Create blog folder:**
   ```
   mkdir _posts
   ```

2. **Add blog post:**
   Create `_posts/2024-12-15-my-first-post.md`:
   ```markdown
   ---
   layout: default
   title: "My First Blog Post"
   date: 2024-12-15
   ---
   
   Content of your blog post...
   ```

3. **Create blog index** (`blog.md`):
   ```markdown
   ---
   layout: default
   title: Blog
   ---
   
   {% for post in site.posts %}
   ## [{{ post.title }}]({{ post.url | relative_url }})
   *{{ post.date | date: "%B %d, %Y" }}*
   
   {{ post.excerpt }}
   
   [Read more]({{ post.url | relative_url }})
   {% endfor %}
   ```

4. **Add to navigation** in `_config.yml`

### Adding Custom Pages

1. **Create new file:** `newpage.md`
   ```markdown
   ---
   layout: default
   title: New Page
   ---
   
   Content here...
   ```

2. **Add to navigation** in `_config.yml`:
   ```yaml
   navigation:
     - title: New Page
       url: /newpage.html
   ```

### Using a Different Layout

1. **Create new layout** in `_layouts/simple.html`:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>{{ page.title }}</title>
   </head>
   <body>
       {{ content }}
   </body>
   </html>
   ```

2. **Use in page:**
   ```markdown
   ---
   layout: simple
   title: Special Page
   ---
   ```

## 🐛 Troubleshooting

### Site not updating after push
- GitHub Pages can take 1-5 minutes to rebuild
- Check the Actions tab in your GitHub repository for build status
- Clear your browser cache

### Images not displaying
- Check file paths (case-sensitive!)
- Ensure images are in `/assets/images/`
- Use `{{ '/assets/images/photo.jpg' | relative_url }}` in templates

### Navigation links broken
- Make sure URLs in `_config.yml` end with `.html`
- Check that corresponding `.md` files exist
- Links are case-sensitive

### Changes to `_config.yml` not showing
- You must restart Jekyll server: `Ctrl+C` then `jekyll serve`
- Changes to other files reload automatically

### Person photos too large/small
- Adjust in `assets/css/style.css`:
  ```css
  .person-card img {
      width: 100px;  /* Change from 80px */
      height: 100px;
  }
  ```

## 📚 Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Liquid Template Language](https://shopify.github.io/liquid/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test locally: `jekyll serve`
5. Commit: `git commit -am 'Add new feature'`
6. Push: `git push origin feature-name`
7. Create a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 📧 Contact

For questions or support, contact: contact@university.edu

---

**Last updated:** December 2024  
**Jekyll version:** 4.x  
**GitHub Pages:** Enabled

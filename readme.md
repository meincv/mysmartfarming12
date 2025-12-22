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
├── _includes/                  # Reusable HTML components
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
│       ├── logo.png           # Logo overlay on header
│       ├── people/            # Team member photos
│       │   ├── e.jpeg         # Ehsan's photo
│       │   ├── f.jpeg         # Florian's photo
│       │   ├── g.jpeg         # Georg's photo
│       │   ├── h.jpeg         # Harsha's photo
│       │   ├── j.jpeg         # Jessica's photo
│       │   ├── l.jpeg         # Leonie's photo
│       │   └── m.jpeg         # Marco's photo
│       └── research/          # Research project images
│           ├── wd.jpg         # Weed Detection
│           ├── am.jpg         # Animal Monitoring
│           ├── gp.jpg         # Genotype-Phenotype
│           ├── pb.jpg         # Plant Disease
│           ├── sb.jpg         # smartBattery
│           └── sr.jpg         # smartReForest
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

### 3. Header Image and Logo Overlay

The site features a full-width header image with a logo overlay in the top-left corner.

#### Changing the Header Image

Replace `/assets/images/header.jpg` with your own image:

- **Recommended size:** 1600x800px (or any 2:1 aspect ratio)
- **Format:** JPG, PNG, or WebP
- **Keep the filename** as `header.jpg` or update `_config.yml`:

```yaml
header_image: /assets/images/your-new-header.jpg
```

#### Adding/Changing the Logo

1. Add your logo to `/assets/images/logo.png`
2. **Recommended size:** 150x150px (or larger, maintains aspect ratio)
3. **Format:** PNG (for transparency) or JPG
4. Logo appears in top-left corner of header with a drop shadow

#### Adjusting Logo Position

Edit `assets/css/style.css`:

```css
.logo-overlay {
    position: absolute;
    top: 20px;          /* Distance from top - change as needed */
    left: 20px;         /* Distance from left - change as needed */
    z-index: 10;
}

.logo-overlay img {
    width: 150px;       /* Adjust logo size */
    height: auto;
}
```

#### Mobile Logo Adjustments

The logo automatically scales down on mobile devices:

```css
@media (max-width: 600px) {
    .logo-overlay {
        top: 10px;
        left: 10px;
    }
    
    .logo-overlay img {
        width: 80px;    /* Smaller on mobile */
    }
}
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

## 🔬 Managing Research Projects

The research page features a custom layout with alternating image positions for a modern, engaging presentation.

### Adding a New Research Project

1. **Add project image** to `/assets/images/research/`:
   - Filename: descriptive name (e.g., `ai-crop-monitoring.jpg`)
   - **Recommended size:** 300x200px to 600x400px
   - **Format:** JPG or PNG
   - **Style:** Should work well with rounded corners and drop shadow

2. **Add project to** `research.md`:

```markdown
### Your Project Title

<div class="research-project image-left">
  <img src="{{ '/assets/images/research/your-image.jpg' | relative_url }}" alt="Project Name" class="project-image">
  <div class="project-content">
    <h4>Project Subtitle or Focus</h4>
    <p><strong>Researcher:</strong> Dr. Your Name</p>
    <p><strong>Project Duration:</strong> January 2024 - December 2026</p>
    <p><strong>Challenge:</strong> Describe the problem you're addressing...</p>
    <p><strong>Approach:</strong> Explain your methodology and techniques...</p>
    <p><strong>Impact:</strong> Describe the expected outcomes and benefits...</p>
  </div>
</div>

---
```

### Alternating Image Layout

The research page uses alternating image positions for visual interest:

- **Image on left:** Use class `image-left`
- **Image on right:** Use class `image-right`

**Pattern for consistency:**
```markdown
<!-- First project - image left -->
<div class="research-project image-left">
  ...
</div>

---

<!-- Second project - image right -->
<div class="research-project image-right">
  ...
</div>

---

<!-- Third project - image left -->
<div class="research-project image-left">
  ...
</div>
```

### Customizing Project Card Styling

Edit `assets/css/style.css`:

```css
/* Change image size */
.research-project .project-image {
    width: 200px;  /* Change from 150px */
    height: auto;
}

/* Adjust spacing between image and text */
.research-project {
    gap: 2rem;     /* Change from 1.5rem */
}

/* Modify image corners */
.research-project .project-image {
    border-radius: 12px;  /* More rounded corners */
}

/* Change shadow effect */
.research-project .project-image {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);  /* Stronger shadow */
}
```

### Mobile Responsive Behavior

On mobile devices, research projects automatically stack vertically with images centered:

```css
@media (max-width: 600px) {
    .research-project,
    .research-project.image-left,
    .research-project.image-right {
        flex-direction: column;  /* Stack vertically */
        align-items: center;     /* Center content */
    }
}
```

## 📝 Updating Content Pages

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

### Teaching Page (`teaching.md`)

The teaching page includes detailed course information organized by semester.

#### Adding a New Course

```markdown
### Winter Semester 2025-2026

**Your New Course Name**
- **Lectures:** Prof. Dr. Your Name
- **Exercises:** Teaching Assistant Name
- Brief description of the course content and learning objectives
```

#### Adding a New Semester Section

```markdown
---

### Summer Semester 2027

**Course 1**
- **Lecturer:** Name
- Description...

**Course 2**
- **Co-lecturer:** Name
- Description...
```

#### Updating Programme Information

To modify the Master's programme details, edit the programme overview section:

```markdown
## Master's Programme: Your Programme Name

**Focus Areas:**
- Topic 1
- Topic 2
- Topic 3

**Key Facts:**
- **Language of instruction:** English/German
- **Duration:** X semesters (XXX ECTS)
- **Location:** Your Campus
- **Start:** Winter/Summer semester
- **Application deadline:** Date

**Further Information:**  
🔗 [www.youruni.edu/programme](http://www.youruni.edu/programme)  
✉️ [contact@youruni.edu](mailto:contact@youruni.edu)
```

### Positions Page (`positions.md`)

The positions page includes both job openings and thesis topics.

#### Adding a Job Opening

```markdown
## Current Opportunities

### Position Title

**Offered by:** Department/Group  
**Duration:** Contract length  
**Start date:** Expected start  

**Description:**  
Detailed description of the position...

**Requirements:**
- Requirement 1
- Requirement 2
- Requirement 3

**To Apply:**  
📩 Send your application to [email@university.edu](mailto:email@university.edu)

---
```

#### Adding a Master's Thesis Topic

```markdown
### 🎓 Topic Number: Your Thesis Title

**Offered by:**  
Supervisor Name  

**Supervisors:**  
- Prof. Dr. Primary Supervisor  
- Dr. Co-Supervisor  

**Description:**  
Detailed description of the research topic, including:
- Research questions
- Methods to be used
- Expected outcomes

📩 *For more details, please contact [supervisor@university.edu](mailto:supervisor@university.edu).*

---
```

#### Indicating No Open Positions

```markdown
## Current Opportunities

> **No open PhD / Postdoc / HiWi positions at the moment**

---
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
  *{{ paper.venue }}* {% if paper.link %}[Link]({{ paper.link }}){% endif %}
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

---
**December 2024:** We received a grant from...

---

**November 2024:** New paper accepted at...

---

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
---
**{{ item.date | date: "%B %Y" }}:** {{ item.description }}

{% endfor %}

---

*Stay updated with our latest research breakthroughs, grants awarded, publications, and group achievements.*
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

For a more structured gallery, create a folder `/assets/images/gallery/` and organize by categories.

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

### Customizing Header and Logo

#### Making Header Taller/Shorter

```css
.header-image {
    height: 400px;  /* Fixed height instead of auto */
}

.header-image img {
    object-fit: cover;  /* Crop to fit container */
}
```

#### Hiding Logo on Mobile

```css
@media (max-width: 600px) {
    .logo-overlay {
        display: none;  /* Hide logo completely on mobile */
    }
}
```

#### Changing Logo Background

```css
.logo-overlay img {
    background-color: rgba(255, 255, 255, 0.9);  /* Semi-transparent white */
    padding: 10px;
    border-radius: 8px;
}
```

## 📸 Image Guidelines

### Header Image
- **Dimensions:** 1600x800px (2:1 ratio recommended)
- **File size:** Under 500KB for fast loading
- **Format:** JPG (for photos) or PNG (for graphics)
- **Location:** `/assets/images/header.jpg`
- **Content:** Choose images that represent your research area

### Logo
- **Dimensions:** 150x150px or larger (maintains aspect ratio)
- **Format:** PNG (recommended for transparency) or SVG
- **Style:** Should be clearly visible against header image
- **Location:** `/assets/images/logo.png`

### People Photos
- **Dimensions:** 200x200px minimum
- **Display size:** 80x80px (automatically resized)
- **Format:** JPEG or PNG
- **Style:** Professional headshots work best
- **Aspect ratio:** 1:1 (square) for circular display
- **Location:** `/assets/images/people/`

### Research Project Images
- **Dimensions:** 300x200px to 600x400px
- **Display size:** 150px width (height auto)
- **Format:** JPG or PNG
- **Style:** Clear, representative images of research
- **Aspect ratio:** Flexible (height adjusts automatically)
- **Location:** `/assets/images/research/`

### General Images
- **Optimize** images before uploading (use tools like TinyPNG)
- **Naming:** Use lowercase with hyphens (e.g., `lab-meeting-2024.jpg`)
- **Alt text:** Always provide descriptive alt text for accessibility

## 🔧 Advanced Customization

### Adding Custom CSS Classes

You can add custom styling for specific elements:

```css
/* Add to assets/css/style.css */

/* Highlight boxes for important information */
.highlight-box {
    background-color: #f5f5f5;
    border-left: 4px solid #333;
    padding: 1rem;
    margin: 1.5rem 0;
}

/* Call-to-action buttons */
.cta-button {
    display: inline-block;
    background-color: #333;
    color: #fff;
    padding: 0.5rem 1.5rem;
    text-decoration: none;
    border-radius: 4px;
}

.cta-button:hover {
    background-color: #555;
}
```

Use in Markdown:
```markdown
<div class="highlight-box">
  <strong>Important Notice:</strong> Applications due by January 31, 2025
</div>

<a href="/positions.html" class="cta-button">View Open Positions</a>
```

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
   
   ---
   {% endfor %}
   ```

4. **Add to navigation** in `_config.yml`

### Creating Custom Page Layouts

1. **Create new layout** in `_layouts/fullwidth.html`:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>{{ page.title }} | {{ site.title }}</title>
       <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
       <style>
           /* Override max-width for full-width layout */
           main {
               max-width: 100%;
               padding: 2rem;
           }
       </style>
   </head>
   <body>
       <main>
           <h1>{{ page.title }}</h1>
           {{ content }}
       </main>
   </body>
   </html>
   ```

2. **Use in page:**
   ```markdown
   ---
   layout: fullwidth
   title: Gallery
   ---
   
   Your full-width content here...
   ```

### Adding Interactive Elements

For simple interactivity without JavaScript:

```markdown
<!-- Accordion/Collapsible content -->
<details>
<summary>Click to expand: Course Details</summary>

**Course Content:**
- Topic 1
- Topic 2
- Topic 3

**Prerequisites:**
- Requirement 1
- Requirement 2
</details>
```

### Adding Video Embeds

```markdown
<!-- YouTube video -->
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" 
          src="https://www.youtube.com/embed/VIDEO_ID" 
          frameborder="0" 
          allowfullscreen>
  </iframe>
</div>
```

## 🐛 Troubleshooting

### Site not updating after push
- GitHub Pages can take 1-5 minutes to rebuild
- Check the Actions tab in your GitHub repository for build status
- Clear your browser cache (Ctrl+F5 or Cmd+Shift+R)

### Images not displaying
- Check file paths (case-sensitive!)
- Ensure images are in `/assets/images/`
- Use `{{ '/assets/images/photo.jpg' | relative_url }}` in templates
- Verify image file extensions match exactly

### Navigation links broken
- Make sure URLs in `_config.yml` end with `.html`
- Check that corresponding `.md` files exist
- Links are case-sensitive

### Changes to `_config.yml` not showing
- You must restart Jekyll server: `Ctrl+C` then `jekyll serve`
- Changes to other files reload automatically

### Person/Research images too large/small
- Adjust in `assets/css/style.css`:
  ```css
  .person-card img {
      width: 100px;  /* Change from 80px */
      height: 100px;
  }
  
  .research-project .project-image {
      width: 200px;  /* Change from 150px */
  }
  ```

### Logo not displaying or misaligned
- Verify logo file exists at `/assets/images/logo.png`
- Check logo positioning in CSS:
  ```css
  .logo-overlay {
      top: 20px;
      left: 20px;
  }
  ```
- Ensure logo has transparent background (use PNG)

### Mobile layout issues
- Test responsiveness using browser dev tools (F12)
- Check mobile-specific CSS in `@media` queries
- Verify images scale properly on small screens

### Research project layout broken
- Ensure you're using correct class names: `image-left` or `image-right`
- Verify image paths are correct
- Check that `<div>` tags are properly closed

## 📚 Jekyll Liquid Template Reference

### Common Template Tags

```liquid
<!-- Variables -->
{{ site.title }}              # Site title from _config.yml
{{ page.title }}              # Current page title
{{ content }}                 # Page content

<!-- Loops -->
{% for item in site.data.people.pi %}
  {{ item.name }}
{% endfor %}

<!-- Conditionals -->
{% if page.title == "Home" %}
  Welcome message
{% endif %}

<!-- Filters -->
{{ site.time | date: "%Y" }}              # Format date
{{ page.url | relative_url }}             # Make URL relative
{{ "/assets/image.jpg" | relative_url }}  # Prepend baseurl
```

### Useful Filters

```liquid
{{ "hello" | capitalize }}        # Hello
{{ "HELLO" | downcase }}          # hello
{{ site.posts | size }}           # Count items
{{ page.content | strip_html }}  # Remove HTML tags
```

## 📄 File Naming Conventions

### Best Practices

- **Markdown files:** `lowercase-with-hyphens.md`
- **Image files:** `descriptive-name.jpg`
- **Data files:** `descriptive_name.yml`
- **CSS files:** `style.css` (single file recommended)
- **Avoid:** Spaces, special characters, uppercase in filenames

### Organizing Large Projects

```
assets/images/
├── research/
│   ├── project1/
│   │   ├── overview.jpg
│   │   ├── diagram.png
│   │   └── results.jpg
│   └── project2/
│       └── ...
├── gallery/
│   ├── 2024/
│   └── 2023/
└── team/
    ├── current/
    └── alumni/
```

## 🚀 Performance Optimization

### Image Optimization

1. **Use appropriate formats:**
   - JPG for photographs
   - PNG for graphics with transparency
   - SVG for logos and icons

2. **Compress images:**
   - Use [TinyPNG](https://tinypng.com/) or [Squoosh](https://squoosh.app/)
   - Target under 200KB for research images
   - Target under 500KB for header images

3. **Responsive images (optional):**
   ```html
   <img srcset="/assets/images/photo-small.jpg 400w,
                /assets/images/photo-medium.jpg 800w,
                /assets/images/photo-large.jpg 1200w"
        src="/assets/images/photo-medium.jpg"
        alt="Description">
   ```

### Minifying CSS (Advanced)

For production, consider minifying your CSS:

1. Use [CSS Minifier](https://cssminifier.com/)
2. Save as `style.min.css`
3. Update `_layouts/default.html`:
   ```html
   <link rel="stylesheet" href="{{ '/assets/css/style.min.css' | relative_url }}">
   ```

## 📧 Contact Forms

### Simple Mailto Link

```markdown
**Contact us:** [email@university.edu](mailto:email@university.edu?subject=Website%20Inquiry)
```

### Using Formspree (Recommended)

1. Sign up at [Formspree.io](https://formspree.io/)
2. Add form to your page:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
  <label>
    Your email:
    <input type="email" name="email" required>
  </label>
  <label>
    Your message:
    <textarea name="message" required></textarea>
  </label>
  <button type="submit">Send</button>
</form>
```

3. Style in `style.css`:

```css
form {
    max-width: 600px;
}

form input, form textarea {
    width: 100%;
    padding: 0.5rem;
    margin-bottom: 1rem;
    border: 1px solid #ddd;
}

form button {
    background-color: #333;
    color: white;
    padding: 0.5rem 2rem;
    border: none;
    cursor: pointer;
}
```

## 🔐 Security Best Practices

### Never Commit Sensitive Information

- Don't include API keys in `_config.yml`
- Don't commit email passwords
- Use environment variables for sensitive data

### Gitignore Recommendations

Create/edit `.gitignore`:

```
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata
.DS_Store
Gemfile.lock
```

## 📊 Analytics (Optional)

### Adding Google Analytics

1. Get your GA tracking ID
2. Create `_includes/analytics.html`:

```html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_TRACKING_ID');
</script>
```

3. Include in `_layouts/default.html` before `</head>`:

```html
{% if jekyll.environment == "production" %}
  {% include analytics.html %}
{% endif %}
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test locally: `jekyll serve`
5. Commit: `git commit -am 'Add new feature'`
6. Push: `git push origin feature-name`
7. Create a Pull Request

## 📋 Checklist for New Site Setup

- [ ] Update `_config.yml` with your information
- [ ] Replace header image (`/assets/images/header.jpg`)
- [ ] Add your logo (`/assets/images/logo.png`)
- [ ] Update homepage content (`index.md`)
- [ ] Add team members in `_data/people.yml`
- [ ] Add team photos to `/assets/images/people/`
- [ ] Update research projects (`research.md`)
- [ ] Add research images to `/assets/images/research/`
- [ ] Update teaching information (`teaching.md`)
- [ ] Update or remove news items (`news.md`)
- [ ] Update positions page (`positions.md`)
- [ ] Test all navigation links
- [ ] Test mobile responsiveness
- [ ] Optimize all images
- [ ] Update contact information throughout
- [ ] Test locally before pushing
- [ ] Push to GitHub and verify deployment

## 📚 Additional Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Liquid Template Language](https://shopify.github.io/liquid/)
- [CSS Tricks](https://css-tricks.com/)
- [Web Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

## 📄 License

This project is open source and available under the MIT License.

## 📧 Support

For questions or support:
- **Technical issues:** Open an issue on GitHub
- **General inquiries:** [your-email@university.edu](mailto:your-email@university.edu)

---

**Last updated:** December 2024  
**Jekyll version:** 4.x  
**GitHub Pages:** Enabled
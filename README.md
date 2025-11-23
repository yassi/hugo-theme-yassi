# Yassi Theme

A modern, minimal Hugo theme with a focus on readability and clean design. Features a timeline-style blog layout, dark mode support, and flexible project showcase options.

example site: [yassi.dev](https://yassi.dev)

## Features

### Dark Mode
- Toggle between light and dark themes
- Persistent user preference (stored in localStorage)
- Smooth transitions between themes
- Colored icons (yellow sun, blue moon)

### Featured Projects
Choose between two display modes for your projects:

**Carousel Mode** (default)
- Horizontal scrolling carousel
- Shows 3 projects at a time on desktop
- Mobile-optimized with peek effect
- Mouse drag and touch swipe support
- Navigation buttons

**Grid Mode**
- 3-column grid on desktop
- Responsive layout for all screen sizes
- Clean card-based design

Configure via `hugo.toml`:
```toml
[params]
  useProjectCarousel = true  # false for grid mode
```

### Timeline Blog Layout
- Vertical timeline with chronological flow
- Interactive dots that highlight on hover
- Dates positioned on the left
- Category badges for each post
- Clean, scannable design
- Mobile-responsive with adapted layout

### Taxonomy Features
- **Word Cloud Display** - Tags and categories shown as weighted word clouds
- **Badge-Style Terms** - Categories and tags displayed as colored badges on single posts
- **Category Display** - Post listings show categories with each post
- **Clickable Terms** - All taxonomy terms link to their respective pages

### Social Media Integration
Configurable social media links with icons:
- GitHub
- Twitter/X
- Facebook
- LinkedIn
- Instagram
- TikTok
- Snapchat

Each icon features brand-specific hover colors.

### Typography & Design
- Clean, readable typography based on Mulish font family
- Article typesetting optimized for long-form content
- Responsive images and media
- Syntax highlighting support
- Proper heading hierarchy

### Responsive Design
- Mobile-first approach
- Hamburger menu for mobile navigation
- Adaptive layouts for all screen sizes
- Touch-friendly interface elements
- Optimized for tablets and desktop

### Navigation
- Clean header with brand section
- Responsive navigation menu
- Sticky footer
- Mobile sidebar navigation
- Smooth transitions and hover effects

## Installation

1. Add the theme to your Hugo site:

```bash
cd your-hugo-site
git submodule add https://github.com/yourusername/yassi.git themes/yassi
```

2. Update your `hugo.toml`:

```toml
theme = "yassi"
```

## Configuration

### Basic Configuration

```toml
baseURL = "https://example.com/"
languageCode = "en-us"
title = "Your Site Title"
theme = "yassi"

[params]
  CoverImage = "/path/to/cover-image.jpg"
  CoverImageWidth = 150
  
  # Project display mode
  useProjectCarousel = true  # or false for grid
  
  # Social Media Links
  [params.social]
    github = "https://github.com/yourusername"
    twitter = "https://twitter.com/yourusername"
    linkedin = "https://linkedin.com/in/yourusername"
    facebook = "https://facebook.com/yourusername"
    instagram = "https://instagram.com/yourusername"
    tiktok = "https://tiktok.com/@yourusername"
    snapchat = "https://snapchat.com/add/yourusername"
```

### Project Front Matter

Create projects in `content/projects/`:

```toml
+++
title = "Project Name"
date = 2024-01-01
summary = "Brief description of your project"
main_image = "/images/project-cover.jpg"
project_url = "https://external-project-url.com"  # optional
featured = true  # Show in featured section
weight = 1  # Order in featured section (lower = first)
+++

Project content here...
```

### Post Front Matter

Create posts in `content/posts/`:

```toml
+++
title = "Post Title"
date = 2024-01-01
summary = "Post subtitle or summary"
main_image = "/images/post-cover.jpg"  # optional
tags = ["tag1", "tag2"]
categories = ["category1"]
+++

Post content here...
```

## Content Organization

```
content/
├── _index.md          # Home page content
├── about.md           # About page
├── posts/             # Blog posts
│   └── my-post.md
└── projects/          # Projects
    └── my-project.md
```

## Customization

### Colors

The theme uses CSS variables for easy customization. Override these in your `assets/css/custom.css`:

```css
:root {
  --link-color: #47b1db;
  --bg-primary: #ffffff;
  --text-primary: #111;
  /* ... more variables */
}
```

### Taxonomies

The theme supports Hugo's taxonomy system. Configure in `hugo.toml`:

```toml
[taxonomies]
  tag = "tags"
  category = "categories"
```

## Features in Detail

### Featured Projects

Control which projects appear in the featured section:
1. Set `featured = true` in project front matter
2. Use `weight` parameter to control order (1, 2, 3...)
3. Projects without `featured = true` won't appear in the featured section
4. All projects still appear on the `/projects/` page

### Dark Mode

The theme automatically:
- Detects system preference on first visit
- Saves user's choice to localStorage
- Applies smooth transitions between themes
- Updates all UI elements including code blocks

### Timeline Layout

The timeline automatically:
- Orders posts chronologically
- Shows dates on the left (desktop) or top (mobile)
- Displays interactive dots at each entry
- Truncates summaries to 2 lines
- Shows category badges

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## License

MIT License - feel free to use and modify as needed.

## Credits

Built with [Hugo](https://gohugo.io/) - the world's fastest static site generator.

# Yassi Theme

A modern, minimal Hugo theme with a focus on readability and clean design. Features a timeline-style blog layout, dark mode support, and flexible project showcase options.

Example site: [yassi.dev](https://yassi.dev)

## Screenshots

<table>
  <tr>
    <td width="50%">
      <img src="/images/screenshot-light.png" alt="Light Mode Screenshot" />
      <p align="center"><b>Light Mode</b></p>
    </td>
    <td width="50%">
      <img src="/images/screenshot-dark.png" alt="Dark Mode Screenshot" />
      <p align="center"><b>Dark Mode</b></p>
    </td>
  </tr>
</table>

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
- **Optional project integration** - Show selected projects alongside posts with visual distinction
- **Optional timeline starting point** - Add a custom message at the end of your timeline
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

### Google Analytics Integration
- Built-in Google Analytics 4 (GA4) support
- Easy configuration with measurement ID
- Uses Hugo's internal analytics template

### Comments with Giscus
- Optional comment system powered by GitHub Discussions
- Lightweight and privacy-friendly
- Dynamically syncs with site's light/dark theme toggle
- Instant theme switching without page reload
- Fully configurable through hugo.toml
- Easy on/off toggle

### Search
- Optional fuzzy search powered by Fuse.js
- Search icon in navbar
- Modal interface with keyboard shortcuts
- Searches posts, projects, and content
- Real-time search results
- Keyboard navigation (/, Cmd/Ctrl+K to open, ESC to close)

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

[services]
  [services.googleAnalytics]
    ID = "G-XXXXXXXXXX"  # Your GA4 measurement ID

[params]
  CoverImage = "/images/avatar.svg"  # or your own image
  CoverImageWidth = 150
  
  # Theme Colors
  # Accent color used for site title underline, timeline bullets, and project cards
  accentColor = "#47b1db"  # Light blue (default)
  accentColorDark = "#5fc9f0"  # Lighter blue for dark mode
  
  # Project display mode
  useProjectCarousel = true  # or false for grid
  
  # Search
  enableSearch = true  # Enable site search with Fuse.js
  
  # Timeline Starting Point (optional)
  timelineStart = "🚀 And so it begins..."
  timelineStartSubText = "Additional context or details..."  # optional
  timelineStartDate = "Jan 2023"  # optional
  
  # Social Media Links
  [params.social]
    github = "https://github.com/yourusername"
    twitter = "https://twitter.com/yourusername"
    linkedin = "https://linkedin.com/in/yourusername"
    facebook = "https://facebook.com/yourusername"
    instagram = "https://instagram.com/yourusername"
    tiktok = "https://tiktok.com/@yourusername"
    snapchat = "https://snapchat.com/add/yourusername"
  
  # Giscus Comments (optional)
  [params.giscus]
    enabled = true
    repo = "yourusername/your-comments-repo"
    repoId = "R_xxxxxxxxxxxxx"
    category = "Announcements"
    categoryId = "DIC_xxxxxxxxxxxxx"
    lightTheme = "light"
    darkTheme = "dark"
```

### Project Front Matter

Create projects in `content/projects/`:

```toml
+++
title = "Project Name"
date = 2024-01-01
summary = "Brief description of your project"
main_image = "/images/project-cover.jpg"
categories = ["category1"]  # optional
tags = ["tag1", "tag2"]  # optional

[params]
  project_url = "https://external-project-url.com"  # optional, external link
  featured = true  # Show in featured section on homepage
  weight = 1  # Order in featured section (lower = first)
  showInPostList = true  # Show in timeline lists alongside blog posts
+++

Project content here...
```

**Project Display Options:**
- `featured = true` - Project appears in the featured projects carousel/grid on homepage
- `showInPostList = true` - Project appears in timeline post lists (homepage, category/tag pages) with a "PROJECT" badge to distinguish it from regular posts
- Projects always appear on the `/projects/` page regardless of these settings

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

#### Accent Color (Easiest)

The quickest way to customize the theme color is via `hugo.toml`:

```toml
[params]
  accentColor = "#47b1db"  # Your brand color
  accentColorDark = "#5fc9f0"  # Variant for dark mode
```

This controls:
- Site title underline (normal and hover states)
- Default avatar/cover image color
- Post summary left border
- Timeline bullet borders and fill on hover
- Timeline post title hover color
- Category/tag badge hover colors
- Project card backgrounds (when no image)
- Word cloud hover colors

#### Advanced Color Customization

For more control, override CSS variables in your `assets/css/custom.css`:

```css
:root {
  --link-color: #47b1db;
  --accent-color: #47b1db;
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

### Search

The theme includes optional fuzzy search powered by Fuse.js:

```toml
[outputs]
  home = ["HTML", "RSS", "JSON"]  # Required for search

[params]
  enableSearch = true
```

**Features:**
- Fuzzy search across all posts and projects
- Search by title (40%), content (30%), summary (20%), and section (10%)
- Modal interface with clean design
- Keyboard shortcuts:
  - `/` or `Cmd/Ctrl + K` - Open search
  - `ESC` - Close search
  - `Arrow keys` - Navigate results
- Real-time results as you type
- Shows color-coded section badges (Posts in blue, Projects in green)
- Mobile responsive
- Up to 10 results displayed

The search uses a custom JSON index that includes both posts and projects, powered by the vendored Fuse.js library (Apache 2.0 licensed) for client-side fuzzy searching.

### Google Analytics

The theme includes built-in Google Analytics 4 support. To enable:

1. Get your GA4 Measurement ID from Google Analytics (starts with `G-`)
2. Add it to your `hugo.toml`:

```toml
[services]
  [services.googleAnalytics]
    ID = "G-XXXXXXXXXX"
```

The theme uses Hugo's internal Google Analytics template, which automatically includes the tracking script in production builds only (not when running `hugo server` locally).

### Comments with Giscus

The theme supports [Giscus](https://giscus.app/), a comments system powered by GitHub Discussions. Giscus is lightweight, privacy-friendly, and automatically adapts to your site's light/dark theme.

**To enable Giscus comments:**

1. Visit [giscus.app](https://giscus.app/) and follow the setup instructions
2. Enable GitHub Discussions in your repository
3. Install the Giscus app on your repository
4. Configure the values in your `hugo.toml`:

```toml
[params.giscus]
  enabled = true
  repo = "yourusername/your-comments-repo"
  repoId = "R_xxxxxxxxxxxxx"
  category = "Announcements"
  categoryId = "DIC_xxxxxxxxxxxxx"
  mapping = "pathname"  # How to map pages to discussions
  strict = "0"  # Use strict title matching
  reactionsEnabled = "1"  # Enable reactions for the main post
  emitMetadata = "0"  # Emit discussion metadata
  inputPosition = "top"  # Comment box position (top or bottom)
  lightTheme = "light"  # Theme for light mode
  darkTheme = "dark"  # Theme for dark mode
  lang = "en"  # Language
  loading = "lazy"  # Lazy load comments
```

**Configuration Options:**

- `enabled` - Set to `true` to enable comments, `false` to disable
- `repo` - Your GitHub repository in the format "username/repo"
- `repoId` - Your repository ID (get from giscus.app)
- `category` - The discussion category to use
- `categoryId` - The category ID (get from giscus.app)
- `mapping` - How URLs map to discussions (pathname, URL, title, etc.)
- `lightTheme` - Giscus theme for light mode (default: "light"). See [available themes](https://github.com/giscus/giscus/blob/main/ADVANCED-USAGE.md#data-theme)
- `darkTheme` - Giscus theme for dark mode (default: "dark"). See [available themes](https://github.com/giscus/giscus/blob/main/ADVANCED-USAGE.md#data-theme)
- All other parameters have sensible defaults and are optional

**Dynamic Theme Switching:**

The theme automatically synchronizes giscus comments with your site's light/dark mode toggle. When users switch between light and dark mode, the comments section will update instantly to match. You can customize the giscus themes used for each mode with the `lightTheme` and `darkTheme` parameters.

Comments will appear at the bottom of all individual post and project pages. To disable comments, simply set `enabled = false` or remove the entire `[params.giscus]` section.

## Features in Detail

### Featured Projects

Control which projects appear in the featured section:
1. Set `featured = true` in project front matter
2. Use `weight` parameter to control order (1, 2, 3...)
3. Projects without `featured = true` won't appear in the featured section
4. All projects still appear on the `/projects/` page

### Projects in Timeline Lists

You can optionally display projects alongside blog posts in timeline views:

1. Add `showInPostList = true` to the `[params]` section of a project's front matter
2. The project will appear in:
   - Homepage post timeline
   - Category pages (for categories assigned to the project)
   - Tag pages (for tags assigned to the project)
   - RSS feeds
3. Projects are visually distinguished with a "PROJECT" badge
4. Timeline lists are sorted by date with newest items first

This is useful for highlighting major projects as part of your content timeline while keeping them separate from regular blog posts.

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

### Timeline Starting Point

You can optionally add a custom message at the end of your timeline (the oldest position) to mark the beginning of your blog:

```toml
[params]
  timelineStart = "🚀 This is where it all began..."
  timelineStartSubText = "Additional context or details..."  # optional
  timelineStartDate = "Jan 2023"  # optional
```

This appears as a non-clickable entry at the end of your timeline with a subtle style. Both text fields support markdown formatting. All parameters are optional - omit `timelineStart` to not show a starting point.

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

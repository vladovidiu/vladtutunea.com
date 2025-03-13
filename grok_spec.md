## Personal Website Specification

### 1. Project Overview

**Purpose**:  
Build a professional personal website to showcase your experience, host a blog, and include a hidden projects page, enhancing your online presence. The site must be fully responsive, delivering an optimal experience across desktop, tablet, and mobile devices.

**Key Pages**:

- Homepage
- Experience
- Blog

**Core Requirements**:

- Mobile-friendly navigation and layouts
- Fast, secure, and SEO-optimized performance

---

### 2. Page Requirements

#### 2.1 Navigation (Global)

- **Menu Items**: Homepage, Experience, Blog (Projects page excluded from navigation)
- **Design**:
  - Sticky menu fixed at the top of the page
  - **Desktop**: Horizontal menu bar with clear, clickable items
  - **Mobile**: Collapses into a hamburger icon (min. 44x44px for easy tapping), opening a slide-out or dropdown menu
- **Mobile Features**:
  - Menu items spaced generously (min. 48px vertical spacing) for touch interaction
  - Hamburger icon positioned in a consistent, accessible corner (e.g., top-right)
- **Accessibility**:
  - Keyboard navigation support
  - Screen reader compatibility (e.g., ARIA labels for menu toggle)

#### 2.2 Homepage

- **Goal**: Introduce yourself and your brand
- **Hero Section**:
  - **Image**: Professional photo (e.g., 1200x800px on desktop, scaled responsively on mobile using `srcset`)
  - **Text**: Tagline (e.g., “Hi, I’m [Your Name], a [Your Profession] passionate about [Your Focus].”)
  - **CTAs**: Buttons to Experience (“Explore My Work”) and Blog (“Read My Blog”), min. 44x44px for mobile tapping
- **Additional Content**:
  - Brief bio (2-3 sentences)
  - Teasers: Latest blog post and most recent job (title + short description)
- **Mobile Adjustments**:
  - Hero image scales to full-width, maintaining aspect ratio
  - Text and CTAs stack vertically with increased font size (min. 16px) for readability
  - Bio and teasers reformat into a single-column layout with touch-friendly spacing
- **Design**:
  - Clean, modern layout with a neutral color scheme (e.g., whites, grays + one accent color)
  - Subtle fade-in animation for hero section (disabled on mobile if performance impacts load time)

#### 2.3 Experience Page

- **Goal**: Display your professional history in a clear timeline
- **Layout**:
  - **Desktop**: Vertical timeline with job entries alternating left and right of a central line
  - **Mobile**: Single-column stack, no alternating sides, for easy scrolling
- **Job Entry Details**:
  - Job title (bold, min. 18px)
  - Company name (hyperlinked, touch-friendly target area)
  - Dates (e.g., “Jan 2020 – Present”)
  - 3-5 bullet points of achievements (min. 16px text)
- **Additional Feature**:
  - “Download Resume” button (min. 44x44px) linking to a PDF
- **Mobile Adjustments**:
  - Full-width job entries with clear separation (e.g., horizontal lines or 20px spacing)
  - Timeline dots or connectors remain visible but simplified
- **Design**:
  - Minimalistic with an accent color for timeline elements
  - Generous white space for readability

#### 2.4 Blog Page

- **Goal**: Present blog posts in an engaging, navigable format
- **Layout**:
  - **Desktop**: 2-3 column grid of cards
  - **Mobile**: Single-column stack for smooth scrolling
- **Card Details**:
  - Featured image (e.g., 600x400px, optimized with lazy loading)
  - Title (bold, clickable, min. 18px)
  - Excerpt (2-3 sentences, min. 16px)
  - Tags (clickable, touch-friendly)
  - “Read More” link (min. 44px tap target)
- **Features**:
  - **Search Bar**: Top of page, full-width on mobile
  - **Tag Navigation**: Sidebar on desktop; horizontal scroll or collapsible list on mobile
- **Mobile Adjustments**:
  - Cards stack vertically with 20px spacing
  - Search bar and tags remain easily tappable without zooming
- **Post Management**:
  - CMS (e.g., WordPress) for easy updates
- **Design**:
  - Clean cards with subtle shadows (hover effects disabled on mobile)
  - Consistent typography (e.g., sans-serif like Roboto)

---

### 3. Design and Branding

- **Color Scheme**: Neutral base (whites, grays) with one accent color (e.g., blue)
- **Typography**: Modern sans-serif (e.g., Inter, Roboto, Open Sans), min. 16px base size for mobile readability
- **Aesthetic**: Professional, clean, and approachable
- **Animations**: Subtle (e.g., fade-ins), disabled on mobile if performance is affected
- **Responsiveness**:
  - CSS media queries for breakpoints:
    - Mobile: <768px
    - Tablet: 768-1024px
    - Desktop: >1024px
  - Touch-friendly elements (min. 44x44px tap targets)
- **Performance**:
  - Optimize images (WebP, lazy loading)
  - Minify CSS/JavaScript
  - Aim for <3-second load times
- **Security**:
  - SSL encryption
  - Regular backups

---

### 4. Technical Architecture

#### 4.1 Platform Choice

- **Recommended**: Remix, taliwindcss, shadcn

#### 4.2 Data Handling

- **Blog Posts**:
  - Stored in mdx files
  - Fields: title, content, image, tags, date
- **Experience/Projects**:
  - Static content, updated manually
- **Media**:
  - Stored in CMS library or folder
  - Use `srcset` for responsive images

#### 4.3 Error Handling

- **404 Page**: Custom design with navigation links
- **Server Errors**: Custom pages for CMS-hosted sites

---

### 5. Testing Plan

- **Functionality**:
  - Test all links, buttons, and forms on desktop and mobile
  - Verify blog search and tag filtering
- **Cross-Device**:
  - Test on iOS/Android mobile devices, tablets, and desktop
  - Use BrowserStack for simulation
- **Cross-Browser**:
  - Chrome, Firefox, Safari, Edge
- **Performance**:
  - Target <3-second load times (Google PageSpeed Insights)
- **Accessibility**:
  - Keyboard navigation, screen reader compatibility (test with WAVE)
- **SEO**:
  - Check meta tags, alt text, and clean URLs

---

### 6. Deployment

- **Hosting**:
  - Static: Vercel
- **Domain**: Custom (e.g., `vladtutunea.com`)
- **SSL**: Enable HTTPS

---

### 7. Optional Add-Ons

- **Contact Page**: Form (name, email, message), mobile-optimized fields
- **Social Links**: Footer icons, min. 44x44px for mobile
- **Dark Mode**: Theme toggle, preference saved

---

### 8. Summary

This specification ensures your personal website works flawlessly on desktop and mobile:

- **Navigation**: Sticky menu with a mobile hamburger icon
- **Homepage**: Scalable hero section, stacked content on mobile
- **Experience**: Timeline adapts to a touch-friendly list on mobile
- **Blog**: Grid stacks vertically with tappable elements
- **Projects**: Hidden page with mobile-optimized layout

The design is modern, secure, and fast, providing a developer with everything needed to build a responsive, user-friendly site tailored to your needs.

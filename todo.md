# Personal Website Project Checklist

This checklist is organized into phases that correspond to the implementation plan. Each phase contains specific tasks and subtasks to ensure thoroughness.

---

## Setup

- [ ] **Initialize Remix project**
  - [ ] Run `npx create-remix@latest`
  - [ ] Choose appropriate options (e.g., TypeScript, deployment target: Vercel)
- [ ] **Install and configure Tailwind CSS**
  - [ ] Run `npm install -D tailwindcss`
  - [ ] Initialize Tailwind: `npx tailwindcss init`
  - [ ] Configure `tailwind.config.js` to include Remix's content paths
  - [ ] Add Tailwind directives to `app/styles/global.css`
- [ ] **Install Shadcn components**
  - [ ] Follow the Shadcn installation guide
  - [ ] Initialize Shadcn in the project
- [ ] **Set up basic file structure**
  - [ ] Create `app/routes` directory
  - [ ] Create `app/components` directory
  - [ ] Create `app/styles` directory if needed
- [ ] **Set up version control**
  - [ ] Initialize Git repository
  - [ ] Create `.gitignore` file (include `node_modules`, build artifacts, etc.)

---

## Core Pages

- [ ] **Implement Global Layout and Navigation**
  - [ ] Create `app/root.tsx` with header, main content area (`<Outlet>`), and footer
  - [ ] Add a sticky navigation menu in the header with links to:
    - Homepage (`/`)
    - Experience (`/experience`)
    - Blog (`/blog`)
  - [ ] Implement responsive design:
    - Horizontal menu on desktop (>1024px)
    - Hamburger menu on mobile (<768px) with slide-out or dropdown
  - [ ] Add accessibility features:
    - ARIA labels (e.g., `aria-label="Toggle navigation"`)
    - Keyboard navigation support
- [ ] **Implement Homepage**
  - [ ] Create `app/routes/index.tsx`
  - [ ] Add hero section:
    - Professional photo (e.g., 1200x800px, using `srcset` for responsiveness)
    - Tagline (e.g., “Hi, I’m [Name], a [Profession] passionate about [Focus].”)
    - Call-to-action buttons (min. 44x44px) to Experience and Blog
  - [ ] Add bio section (2-3 sentences, min. 16px text)
  - [ ] Ensure responsive design: stack elements vertically on mobile
- [ ] **Implement Experience Page**
  - [ ] Create `app/routes/experience.tsx`
  - [ ] Add vertical timeline with job entries (static data or JSON)
  - [ ] Implement responsive design:
    - Alternating entries left/right on desktop (>1024px)
    - Stacked vertically on mobile (<768px)
  - [ ] Each job entry includes:
    - Job title (bold, min. 18px)
    - Company name (hyperlinked, touch-friendly)
    - Dates (e.g., “Jan 2020 – Present”)
    - 3-5 bullet points of achievements (min. 16px text)
  - [ ] Add “Download Resume” button (min. 44x44px) linking to a PDF
  - [ ] Add actual job entries with real data
- [ ] **Set Up Blog Post Data Loading**
  - [ ] Create `app/posts` directory with sample MDX files
    - Each file includes title, date, tags, and content
  - [ ] Configure Remix to read MDX files (e.g., using `@mdx-js/rollup`)
  - [ ] Write a loader function to fetch all posts’ metadata (title, date, tags, slug)
- [ ] **Implement Blog Page (List View)**
  - [ ] Create `app/routes/blog.tsx`
  - [ ] Use the loader to fetch posts
  - [ ] Display a list of posts with:
    - Title (min. 18px)
    - Date
    - “Read More” link (min. 44px target) to `/blog/[slug]`
  - [ ] Implement responsive layout:
    - 2-3 column grid on desktop (>1024px)
    - Single column on mobile (<768px)
- [ ] **Enhance Blog Page with Images and Excerpts**
  - [ ] Update post component to include:
    - Featured image (e.g., 600x400px, lazy-loaded)
    - Excerpt (2-3 sentences, min. 16px)
    - Tags (clickable, touch-friendly)
  - [ ] Optimize images with `loading="lazy"` and responsive sizes via `srcset`
- [ ] **Implement Individual Blog Post Pages**
  - [ ] Create `app/routes/blog.$slug.tsx`
  - [ ] Write a loader to fetch and compile the specific MDX file based on the slug
  - [ ] Render the MDX content with Tailwind CSS styling
  - [ ] Ensure responsive design and readability (min. 16px text)
- [ ] **Implement Hidden Projects Page**
  - [ ] Create `app/routes/projects.tsx`
  - [ ] Add a grid or list of static project entries (title, description, link)
  - [ ] Ensure responsive design: stack on mobile
  - [ ] Do not include in navigation; accessible only via direct URL

---

## Features

- [ ] **Add Search and Tag Functionality to Blog Page**
  - [ ] Add a search bar (full-width on mobile) with client-side filtering by title or content
  - [ ] Implement tag navigation:
    - Sidebar on desktop (>1024px)
    - Horizontal scroll or collapsible list on mobile (<768px)
  - [ ] Add tag filtering (client-side)
  - [ ] Ensure touch-friendly targets (min. 44x44px)
- [ ] **Add Teasers to Homepage**
  - [ ] Fetch the latest blog post and most recent job
  - [ ] Display teasers below the bio with titles and short descriptions
  - [ ] Ensure responsive layout
- [ ] **Implement Additional Features**
  - [ ] **Contact Page**
    - [ ] Create `app/routes/contact.tsx`
    - [ ] Add a form with name, email, and message fields
    - [ ] Implement form validation
    - [ ] Set up form submission (e.g., to email or a backend service)
    - [ ] Ensure mobile-optimized fields
  - [ ] **Social Links**
    - [ ] Add social media icons in the footer (min. 44x44px)
    - [ ] Link to profiles (open in new tabs)
  - [ ] **Dark Mode**
    - [ ] Add a theme toggle button in the header or footer
    - [ ] Implement dark mode using CSS variables or Tailwind’s dark mode
    - [ ] Save user preference (e.g., in localStorage)

---

## Optimization

- [ ] **Optimize Performance and SEO**
  - [ ] Optimize images:
    - Convert to WebP format
    - Use lazy loading
    - Add descriptive alt text
  - [ ] Minify CSS and JS using Remix’s build process
  - [ ] Add meta tags (title, description) for each page
  - [ ] Ensure clean URLs (e.g., `/blog/my-post`)
  - [ ] Implement code splitting if necessary (e.g., dynamic imports for large components)
  - [ ] Target <3-second load times (verify with Google PageSpeed Insights)

---

## Testing

- [ ] **Write and run functionality tests**
  - [ ] Test all links, buttons, and forms across pages
  - [ ] Test blog search and tag filtering functionality
- [ ] **Perform cross-device testing**
  - [ ] Test on mobile, tablet, and desktop devices
  - [ ] Use tools like BrowserStack for device simulation
- [ ] **Perform cross-browser testing**
  - [ ] Test on Chrome, Firefox, Safari, and Edge
- [ ] **Test performance**
  - [ ] Use Google PageSpeed Insights to ensure <3-second load times
- [ ] **Test accessibility**
  - [ ] Verify keyboard navigation works across the site
  - [ ] Check screen reader compatibility (e.g., using WAVE or axe)
- [ ] **Test SEO**
  - [ ] Confirm meta tags, alt text, and clean URLs are properly implemented
- [ ] **Write unit tests**
  - [ ] Test individual components (e.g., navigation, post cards)
  - [ ] Test loader functions for data fetching
- [ ] **Write integration tests**
  - [ ] Test interactions between components (e.g., navigation and page rendering)
  - [ ] Test data flow from loaders to components
- [ ] **Write end-to-end tests**
  - [ ] Test critical user flows (e.g., navigating between pages, submitting forms, viewing blog posts)

---

## Deployment

- [ ] **Deploy to Vercel**
  - [ ] Set up a Vercel project
  - [ ] Connect the Git repository
  - [ ] Configure build settings (e.g., `npm run build`, `npm start`)
- [ ] **Set up custom domain**
  - [ ] Purchase or configure the domain (e.g., `yourname.com`)
  - [ ] Set DNS records to point to Vercel
- [ ] **Enable SSL**
  - [ ] Configure SSL on Vercel for HTTPS
- [ ] **Set up continuous deployment**
  - [ ] Configure Vercel to deploy automatically on pushes to the main branch

---

## Review and Refine

- [ ] **Review the entire checklist for completeness**
- [ ] **Ensure all tasks are actionable and specific**
- [ ] **Add any missing subtasks or details as needed**
- [ ] **Prioritize tasks if necessary (e.g., core pages before optional features)**

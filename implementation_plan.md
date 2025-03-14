## Implementation Plan

### High-Level Blueprint

#### Major Components

- **Frontend**: Built with Remix, Tailwind CSS, and Shadcn for a responsive, modern UI/UX.
- **Backend**: Minimal, as blog posts use MDX files processed via Remix’s static site generation or server-side rendering. No database is required unless optional features (e.g., comments) are added later.
- **Content Management**: Blog posts stored as MDX files, read and rendered by Remix.
- **Deployment**: Hosted on Vercel for static site deployment with SSL.

#### Architecture and Flow

- **Navigation**: A sticky, responsive menu (horizontal on desktop, hamburger on mobile) links to Homepage, Experience, and Blog. The Projects page is hidden but accessible via direct URL.
- **Homepage**: Features a hero section (image, tagline, CTAs), a bio, and teasers for the latest blog post and most recent job.
- **Experience**: A timeline of job entries, alternating on desktop and stacked on mobile, with a resume download link.
- **Blog**: A grid (desktop) or list (mobile) of posts with search and tag filtering, linking to individual post pages rendered from MDX.
- **Projects**: A hidden page showcasing projects in a grid or list format.

#### Key Features

- Fully responsive design with mobile-friendly navigation and touch targets (min. 44x44px).
- Fast load times (<3 seconds) with optimized images (WebP, lazy loading) and minified assets.
- SEO optimization via meta tags, alt text, and clean URLs.
- Security with SSL on Vercel.
- Optional add-ons: contact form, social links, dark mode.

### Iterative Chunks

The project is divided into 14 refined chunks, each building on the previous ones. These chunks are sized to be small enough for safe implementation with testing, yet substantial enough to show progress.

---

## Series of Prompts for Code-Generation LLM

### Chunk 1: Set up the Project

```
**Context**:
You are starting a personal website project using Remix, Tailwind CSS, and Shadcn. The site will include Homepage, Experience, Blog, and a hidden Projects page, with a focus on responsiveness, performance, and SEO.

**Requirements**:
- Initialize a new Remix project using the command-line tool.
- Install and configure Tailwind CSS with its default setup.
- Install Shadcn components and initialize them for use.
- Set up a basic file structure (e.g., `app/routes`, `app/components`).

**Integration Points**:
- This is the foundational setup, with no prior chunks to integrate.

**Testing Requirements**:
- Verify the project builds and runs locally without errors (`npm run dev`).
- Test Tailwind CSS by adding a styled `<div>` (e.g., `className="bg-blue-500 text-white p-4"`) and checking it renders correctly.
- Confirm Shadcn is installed by importing and rendering a sample component (e.g., a button).
```

---

### Chunk 2: Implement Global Layout and Navigation

```
**Context**:
The Remix project is set up with Tailwind CSS and Shadcn. Now, implement a global layout with a responsive navigation menu.

**Requirements**:
- Create a root layout (`app/root.tsx`) with a header, main content area, and footer.
- Implement a sticky navigation menu in the header with links to Homepage (`/`), Experience (`/experience`), and Blog (`/blog`).
- On desktop (>1024px), display a horizontal menu. On mobile (<768px), collapse it into a hamburger menu (min. 44x44px) with a slide-out or dropdown.
- Add accessibility: ARIA labels (e.g., `aria-label="Toggle navigation"`) and keyboard support for the hamburger menu.

**Integration Points**:
- Use Remix’s `<Outlet>` to render page content in the main area.
- Links should use Remix’s `<Link>` for routing.

**Testing Requirements**:
- Check the menu is sticky (scrolling keeps it at the top).
- Verify menu items are clickable and navigate correctly (even if pages are empty).
- Test mobile view: hamburger icon appears, opens/closes the menu, and items are spaced (min. 48px vertically).
- Test keyboard navigation: tab through menu items and toggle the hamburger menu.
- Use a screen reader to confirm accessibility.
```

---

### Chunk 3: Implement the Homepage (Basic)

```
**Context**:
The global layout with navigation is in place. Now, build the basic Homepage with a hero section and bio.

**Requirements**:
- Create a Homepage route (`app/routes/index.tsx`).
- Add a hero section with a professional photo (e.g., 1200x800px, using `srcset` for responsiveness), a tagline (e.g., “Hi, I’m [Name], a [Profession] passionate about [Focus].”), and CTAs to Experience and Blog (min. 44x44px buttons).
- Include a bio section (2-3 sentences).
- Ensure responsiveness: stack elements vertically on mobile (<768px), with min. 16px text.

**Integration Points**:
- Render within the global layout’s `<Outlet>`.
- Link CTAs to `/experience` and `/blog` using `<Link>`.

**Testing Requirements**:
- Verify the hero section displays the image, tagline, and CTAs correctly.
- Check the image scales responsively and bio text is readable on mobile.
- Test CTAs navigate to the correct routes.
- Confirm layout stacks vertically on mobile using browser resizing or emulation.
```

---

### Chunk 4: Implement the Experience Page

```
**Context**:
The Homepage is implemented. Now, build the Experience page with a professional timeline.

**Requirements**:
- Create an Experience route (`app/routes/experience.tsx`).
- Implement a vertical timeline with static job entries (e.g., in a JSON file or hardcoded). On desktop (>1024px), alternate entries left/right of a central line; on mobile (<768px), stack vertically.
- Each entry includes: job title (bold, min. 18px), company name (hyperlinked), dates, and 3-5 bullet points.
- Add a “Download Resume” button (min. 44x44px) linking to a placeholder PDF.
- Ensure responsiveness and touch-friendly spacing (e.g., 20px between entries).

**Integration Points**:
- Accessible via the navigation menu.
- Render within the global layout.

**Testing Requirements**:
- Check the timeline alternates on desktop and stacks on mobile.
- Verify job entry details display correctly and company links work.
- Test the “Download Resume” button opens the PDF.
- Confirm touch interactions and responsiveness on mobile emulation.
```

---

### Chunk 5: Set Up Blog Post Data Loading

```
**Context**:
The Experience page is complete. Now, set up data loading for blog posts stored as MDX files.

**Requirements**:
- Create a directory (e.g., `app/posts`) with sample MDX files containing title, date, tags, and content.
- Configure Remix to read these files using `@mdx-js/rollup` or a similar plugin.
- Write a loader function to fetch all posts’ metadata (title, date, tags, slug) and return it as JSON.

**Integration Points**:
- Prepares data for the Blog page, to be used in the next chunk.

**Testing Requirements**:
- Test the loader fetches metadata for all MDX files correctly.
- Verify metadata parsing (e.g., title matches file content).
- Check error handling for missing or malformed MDX files.
```

---

### Chunk 6: Implement the Blog Page (List View)

```
**Context**:
Blog post data loading is set up. Now, implement the Blog page to list posts.

**Requirements**:
- Create a Blog route (`app/routes/blog.tsx`).
- Use the loader from Chunk 5 to fetch posts.
- Display a list with each post showing title (min. 18px), date, and a “Read More” link (min. 44px target) to `/blog/[slug]`.
- On desktop (>1024px), use a 2-3 column grid; on mobile (<768px), a single column.
- Ensure responsiveness.

**Integration Points**:
- Accessible via the navigation menu.
- Render within the global layout.

**Testing Requirements**:
- Verify the page loads and lists all posts from the loader.
- Check grid layout on desktop and stacking on mobile.
- Test “Read More” links point to correct slugs (even if pages are empty).
```

---

### Chunk 7: Enhance Blog Page with Images and Excerpts

```
**Context**:
The Blog page lists posts. Now, enhance it with images and excerpts.

**Requirements**:
- Update the post component to include a featured image (e.g., 600x400px, lazy-loaded), excerpt (2-3 sentences), and tags.
- Optimize images with `loading="lazy"` and responsive sizes via `srcset`.
- Ensure the layout remains responsive and touch-friendly (20px spacing).

**Integration Points**:
- Enhance the existing Blog page.
- Use loader data, assuming MDX files include image paths and excerpts.

**Testing Requirements**:
- Check each post displays image, excerpt, and tags correctly.
- Verify images lazy-load (e.g., via browser dev tools).
- Confirm layout looks good and is touch-friendly on mobile.
```

---

### Chunk 8: Implement Individual Blog Post Pages

```
**Context**:
The Blog page links to individual posts. Now, implement those dynamic routes.

**Requirements**:
- Create a dynamic route (`app/routes/blog.$slug.tsx`).
- Write a loader to fetch and compile the specific MDX file’s content based on the slug.
- Render the MDX content with Tailwind CSS styling.
- Ensure responsiveness and readability (min. 16px text).

**Integration Points**:
- “Read More” links from the Blog page navigate here.
- Render within the global layout.

**Testing Requirements**:
- Test navigating to a post’s URL displays its content.
- Verify MDX renders with proper styling (e.g., headings, paragraphs).
- Check readability and responsiveness on mobile.
```

---

### Chunk 9: Add Search and Tag Functionality to Blog Page

```
**Context**:
The Blog page displays enhanced posts. Now, add search and tag filtering.

**Requirements**:
- Add a search bar (full-width on mobile) to filter posts by title or content (client-side).
- Implement tag navigation: sidebar on desktop (>1024px), horizontal scroll or collapsible list on mobile (<768px).
- Filter posts by clicked tags (client-side).
- Ensure touch-friendly targets (min. 44x44px).

**Integration Points**:
- Enhance the existing Blog page.
- Use loader data for filtering.

**Testing Requirements**:
- Verify search filters posts as typed.
- Check tag clicks filter posts correctly.
- Test usability of search and tags on desktop and mobile.
```

---

### Chunk 10: Add Teasers to Homepage

```
**Context**:
The Homepage, blog, and experience data are ready. Now, add teasers to the Homepage.

**Requirements**:
- Fetch the latest blog post (from Chunk 5’s loader) and most recent job (from Chunk 4’s data).
- Display teasers with titles and short descriptions below the bio.
- Ensure responsiveness, fitting within the layout.

**Integration Points**:
- Add to the existing Homepage route.
- Use existing data sources.

**Testing Requirements**:
- Check teasers display the latest post and job correctly.
- Verify layout remains responsive with teasers added.
```

---

### Chunk 11: Implement the Hidden Projects Page

```
**Context**:
Core pages are complete. Now, add a hidden Projects page.

**Requirements**:
- Create a Projects route (`app/routes/projects.tsx`).
- Design a grid or list of static project entries (title, description, link).
- Ensure responsiveness (stack on mobile).
- Do not link in navigation.

**Integration Points**:
- Render within the global layout.
- Accessible only via direct URL.

**Testing Requirements**:
- Verify the page isn’t in navigation but loads at `/projects`.
- Check projects display correctly and layout adapts to mobile.
```

---

### Chunk 12: Implement Additional Features

```
**Context**:
The core site is built. Now, add optional features: contact page, social links, and dark mode.

**Requirements**:
- **Contact Page**: Route (`/contact`) with a form (name, email, message), mobile-optimized.
- **Social Links**: Add footer icons (min. 44x44px) linking to profiles.
- **Dark Mode**: Add a toggle in the header/footer, switching themes and saving preference (e.g., localStorage).

**Integration Points**:
- Contact page optional in navigation.
- Social links in global footer.
- Dark mode toggle in global layout.

**Testing Requirements**:
- Test contact form submits and is usable on mobile.
- Verify social links open in new tabs.
- Check dark mode toggles themes and persists preference.
```

---

### Chunk 13: Optimize Performance and SEO

```
**Context**:
The site is functional. Now, optimize for performance and SEO.

**Requirements**:
- Optimize images: convert to WebP, use lazy loading, add alt text.
- Minify CSS/JS with Remix’s build process.
- Add meta tags (title, description) and ensure clean URLs.
- Target <3-second load times.

**Integration Points**:
- Apply across all pages and components.

**Testing Requirements**:
- Use Google PageSpeed Insights to verify <3-second load times.
- Check images have alt text and lazy-load.
- Confirm meta tags render in page source.
```

---

### Chunk 14: Testing and Deployment

```
**Context**:
The site is optimized. Now, test thoroughly and deploy.

**Requirements**:
- Write tests: functionality (links, forms), cross-device (mobile, tablet, desktop), cross-browser (Chrome, Firefox, Safari, Edge), performance (<3s), accessibility (keyboard, screen reader), SEO (meta tags).
- Deploy to Vercel with a custom domain and SSL.

**Integration Points**:
- Tests cover all prior chunks.
- Deployment makes the site live.

**Testing Requirements**:
- Run functionality tests: all interactive elements work.
- Test on multiple devices/browsers via BrowserStack.
- Verify performance with PageSpeed Insights.
- Check accessibility with WAVE.
- Confirm SEO elements are present.
```

---

## Summary

This plan delivers a fully responsive personal website with a Homepage, Experience page, Blog (with search/tags), and hidden Projects page, plus optional features. Each chunk builds incrementally, integrates seamlessly, and includes testing to ensure quality. Deployed on Vercel, the site will be fast, secure, and SEO-optimized, meeting all specification requirements.

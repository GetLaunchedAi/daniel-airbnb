# Project File Structure

This document outlines the complete file structure of the True Heating and Cooling HVAC website project and provides a one-sentence summary of each file's purpose.

## Root Directory

- **.eleventy.js** - Eleventy configuration file that sets up the static site generator, image optimization, navigation plugins, and build settings.
- **.gitignore** - Git ignore file that excludes node_modules, public, .cache, and ImageRetriever folders from version control.
- **info.md** - Client information document containing business details, contact info, services, and unique selling points for True Heating and Cooling.
- **LICENSE.md** - Creative Commons CC0 1.0 Universal license file that releases the code into the public domain.
- **package-lock.json** - Automatically generated file that locks dependency versions for consistent npm installations.
- **package.json** - NPM package configuration defining project dependencies (Eleventy, image plugin, navigation plugin) and build scripts.
- **README.md** - Comprehensive documentation explaining the Eleventy starter kit, features, file structure, and usage instructions.

## src/ (Source Files)

### src/_data/
- **client.json** - Global data file containing client information (name, contact details, address) accessible throughout the site via Nunjucks templating.

### src/_includes/
- **footer.html** - Reusable footer component with navigation links, services list, contact information, and credit section.
- **header.html** - Reusable header component containing the navigation menu with dropdown services menu and dark mode toggle.

### src/_layouts/
- **base.html** - Main layout template that wraps all pages with head meta tags, navigation, footer, and scripts.

### src/admin/
- **config.yml** - Netlify CMS configuration file for content management with Git Gateway backend.
- **index.html** - Entry point HTML file for the Netlify CMS admin interface.

### src/assets/

#### src/assets/favicons/
- **android-chrome-192x192.png** - Android home screen icon at 192x192 resolution.
- **android-chrome-384x384.png** - Android home screen icon at 384x384 resolution.
- **browserconfig.xml** - Browser configuration file for Windows tile icons and theme colors.
- **mstile-150x150.png** - Microsoft tile icon at 150x150 resolution for Windows start menu.
- **site.webmanifest** - Web app manifest file defining how the site appears when installed as a PWA.

#### src/assets/fonts/
- **roboto-v29-latin-700.woff** - Roboto font bold (700 weight) in WOFF format for web use.
- **roboto-v29-latin-700.woff2** - Roboto font bold (700 weight) in WOFF2 format for better compression and modern browsers.
- **roboto-v29-latin-900.woff** - Roboto font black (900 weight) in WOFF format for headers and emphasis.
- **roboto-v29-latin-900.woff2** - Roboto font black (900 weight) in WOFF2 format for optimized loading.
- **roboto-v29-latin-regular.woff** - Roboto font regular weight in WOFF format for body text.
- **roboto-v29-latin-regular.woff2** - Roboto font regular weight in WOFF2 format for modern browsers.

#### src/assets/images/
- **logo-blue.png** - Company logo in blue used throughout the site in header, footer, and favicon.

#### src/assets/js/
- **animations.js** - JavaScript file handling scroll-based animations using Intersection Observer and confetti effects for form submissions.
- **dark.js** - JavaScript implementing dark mode toggle functionality with localStorage persistence and system preference detection.
- **faq.js** - JavaScript for FAQ accordion functionality allowing users to expand/collapse question items.
- **nav.js** - JavaScript controlling mobile navigation hamburger menu and service dropdown menu interactions.

#### src/assets/svgs/
- **cta-squares.svg** - Decorative SVG graphic element used in call-to-action sections.
- **profile-woman.svg** - SVG avatar icon representing a female profile for customer reviews.
- **profile.svg** - SVG avatar icon representing a generic profile for customer reviews.
- **stars.svg** - SVG graphic displaying star rating icons for customer testimonials.
- **sun.svg** - SVG sun icon used in the dark mode toggle button.

### src/css/
- **about.css** - Stylesheet for the About Us page with side-by-side layout and content sections.
- **animations.css** - CSS animations and transitions for scroll effects, fade-ins, and element reveals.
- **contact.css** - Stylesheet for the Contact page featuring form styling and contact information layout.
- **critical.css** - Critical CSS containing essential above-the-fold styles for navigation, hero sections, and core layout.
- **home.css** - Stylesheet for the homepage including hero section, services grid, side-by-side sections, and reviews.
- **projects.css** - Stylesheet for the Projects/Gallery page with responsive image grid layout.
- **reviews.css** - Stylesheet for the Reviews page featuring customer testimonial cards and star ratings.
- **root.css** - Root stylesheet defining CSS custom properties (variables), global styles, typography, and color schemes.
- **services.css** - Stylesheet for service pages including content layouts, FAQ sections, and service-specific components.

### src/images/
- **about-bottom.jpg** - Image used at the bottom of the About page in the call-to-action section.
- **about-us-sq.jpg** - Square format image of HVAC equipment used in About Us page side-by-side sections.
- **aboutus-hero.jpg** - Hero banner image for the About Us page showing HVAC unit exterior.
- **ac-hero.jpg** - Hero banner image for the Air Conditioners service page.
- **ac-mini-split.jpg** - Image showcasing ductless mini-split air conditioning units.
- **ac-modern-unit.jpg** - Image of a modern air conditioning unit installation.
- **boiler-detail.jpg** - Close-up detail image of boiler components and piping.
- **boiler-hero.jpg** - Hero banner image for the Boilers service page.
- **boiler-pipes.jpg** - Image showing boiler pipe installation and connections.
- **furnace-hero.jpg** - Hero banner image for the Furnaces service page showing home in winter.
- **furnace-repair.jpg** - Image of a technician performing furnace repair work.
- **furnace-unit.jpg** - Image of a high-efficiency furnace heating system unit.
- **heat-pump-hero.jpg** - Hero banner image for the Heat Pumps service page.
- **heat-pump-install.jpg** - Image showing heat pump installation process.
- **heat-pump-unit.jpg** - Image of an installed heat pump unit.
- **home-cooling.jpg** - Image representing cooling services for the homepage services section.
- **home-heat-pumps.jpg** - Image of heat pump for the homepage services showcase.
- **home-heating.jpg** - Image representing heating services for the homepage services section.
- **hvac-heating.jpg** - General HVAC heating system image used across multiple pages.
- **hvac-hero.jpg** - Main hero banner image showing HVAC unit installation.
- **hvac-hero.webp** - WebP optimized version of the main hero image for faster loading.
- **hvac-repair.jpg** - Image of HVAC technician performing repair work.
- **newleafmap.png** - Map image (possibly from a previous project, may need updating).
- **water-tank-content.jpg** - Content image for hot water tank services section.
- **water-tank-detail.jpg** - Detail image showing hot water tank components and installation.
- **water-tank-hero.jpg** - Hero banner image for the Hot Water Tanks service page.

#### src/images/portfolio/
- **port1.jpg** - Portfolio gallery image #1 showcasing completed HVAC project.
- **port2.jpg** - Portfolio gallery image #2 showcasing completed HVAC project.
- **port3.jpg** - Portfolio gallery image #3 showcasing completed HVAC project.
- **port4.jpg** - Portfolio gallery image #4 showcasing completed HVAC project.
- **port5.jpg** - Portfolio gallery image #5 showcasing completed HVAC project.
- **port6.jpg** - Portfolio gallery image #6 showcasing completed HVAC project.
- **port7.jpg** - Portfolio gallery image #7 showcasing completed HVAC project.
- **port8.jpg** - Portfolio gallery image #8 showcasing completed HVAC project.
- **port9.jpg** - Portfolio gallery image #9 showcasing completed HVAC project.

### src/pages/
- **_new-page-template.txt** - Template file with frontmatter structure and instructions for creating new pages.
- **about.html** - About Us page featuring company information, certifications, and team details.
- **contact.html** - Contact page with form, email, phone, location, and Facebook link information.
- **projects.html** - Projects gallery page displaying a grid of completed HVAC installation and repair work.
- **reviews.html** - Reviews page showcasing customer testimonials with ratings and profile avatars.
- **services.html** - Main services overview page listing all HVAC services offered by True Heating and Cooling.

#### src/pages/servicepages/
- **air-conditioners.html** - Dedicated service page for air conditioning installation, repair, and maintenance services.
- **boilers.html** - Dedicated service page for boiler installation, repair, and maintenance services.
- **furnaces.html** - Dedicated service page for furnace installation, repair, and seasonal tune-up services.
- **heat-pumps.html** - Dedicated service page for energy-efficient heat pump installation and services.
- **hot-water-tanks.html** - Dedicated service page for hot water tank and tankless water heater services.

### src/ (Root Files)
- **_redirects** - Netlify redirects configuration file (currently empty, ready for URL redirects if needed).
- **index.html** - Homepage featuring hero section, services overview, about section, reviews, and call-to-action.
- **robots.txt** - Search engine robots file that disallows /admin/ directory and points to sitemap.

## Project Summary

This is an Eleventy-based static site for True Heating and Cooling, a Michigan HVAC company offering furnace, boiler, air conditioning, heat pump, and hot water tank services in the Detroit area. The site uses Nunjucks templating, includes dark mode support, features responsive image optimization, and is set up for deployment on Netlify with optional CMS integration.

---
id: design
title: 'Design System & Style Guide'
description: 'Outlines the visual language, color palette, typography, and overall aesthetic for the Alpine Modern design.'
type: doc
subtype: core
status: draft
sequence: 6
tags:
  - design
  - style-guide
  - ui-ux
createdAt: '2024-05-21T10:00:00Z'
updatedAt: '2024-05-21T10:00:00Z'
---

## 1. Design Philosophy: Alpine Modern

The visual identity for the Gasthof Roschitzhof relaunch is encapsulated by the term "Alpine Modern." This is a fusion of rustic authenticity and clean, high-performance design. It's about communicating the warmth and tradition of a Styrian Gasthof through a modern, efficient, and visually stunning digital lens.

*   **Vibe:** Rustic Elegance, Vibrant, Efficient. The design should feel robust and trustworthy, yet also fresh and inviting. We avoid sterile minimalism; instead, we use clean lines to frame rich, high-quality photography and videography.
*   **Core Principles:**
    *   **Content-First:** The design serves the content. Large, immersive images and videos of the landscape, food, and atmosphere are the heroes.
    *   **Clarity and Intent:** Every element has a purpose. Navigation is intuitive, and calls to action are clear and compelling.
    *   **Authenticity:** We use real photography and genuine testimonials. The design should reflect the true character of the Gasthof, not a generic template.

## 2. Color Palette

The color palette is inspired by the natural environment of the Soboth region and the warmth of the Gasthof itself.

*   **Primary Color (`primaryColor`): `#ef4444` (Vibrant Red)**
    *   **Usage:** This is our action color. Used for primary buttons ("Book a Table"), key highlights, and brand accents. It's energetic and confident, reflecting the vibrancy of both the local culture and the motorcycling community.

*   **Accent Color (`accentColor`): `#FFD700` (Gold)**
    *   **Usage:** Used sparingly for secondary CTAs, special highlights, or to denote premium features. It complements the red and adds a touch of elegance and quality, reminiscent of golden hour light or a perfectly cooked schnitzel.

*   **Neutral Dark (`neutralDark`): `#1a202c` (Charcoal)**
    *   **Usage:** The primary color for all body text and dark UI elements. It provides excellent contrast against light backgrounds, ensuring readability. It's a softer, more modern alternative to pure black.

*   **Neutral Light (`neutralLight`): `#f8fafc` (Off-White)**
    *   **Usage:** The primary background color for most sections. It's clean, airy, and provides a neutral canvas that allows the photography and primary colors to stand out.

## 3. Typography

We will use a single, versatile font family to maintain consistency and improve performance.

*   **Font Family (`fontFamily`): Inter**
    *   **Why Inter?** It's a highly legible sans-serif font designed specifically for user interfaces. It works beautifully at all sizes, from large, impactful headlines to small, detailed micro-copy.
    *   **Headlines (H1, H2):** Font weight will be Bold (700) or Extra Bold (800). Example: `"Your Basecamp on the Soboth Pass."`
    *   **Sub-Headlines (H3):** Font weight will be Semi-Bold (600).
    *   **Body Copy:** Font weight will be Regular (400). Sized for optimal readability on both desktop and mobile screens.

## 4. UI Components & Patterns

Consistency in UI elements is key to a predictable and user-friendly experience.

*   **Buttons:**
    *   **Primary:** Solid background (`primaryColor`), white text, subtle hover effect (slight darkening).
    *   **Secondary:** Ghost button style. Transparent background with a `primaryColor` or `accentColor` border and text. The background fills with color on hover.

*   **Cards:**
The "Choose Your Adventure" cards will be the primary navigation pattern. They will feature a high-quality background image with a dark, translucent overlay to ensure the white text on top is legible. A subtle zoom effect on the image on hover will add a touch of interactivity.

*   **Navigation (`navigationPattern`):**
    *   **Desktop:** A clean, traditional navigation bar at the top with a sticky-on-scroll behavior.
    *   **Mobile:** The signature "Thumb Zone" sticky bottom bar (`bottom-tabs`) with icons for the four most critical actions: 📞 Call, 🗺️ Map, 📅 Book, 🍔 Menu. This is a core part of the mobile-first UX strategy.

*   **Imagery:**
All photography must be professional, high-resolution, and authentic. We will focus on capturing the golden hour light, the texture of the food, and the genuine atmosphere of the Gasthof. Videography for the hero loop will be smooth, slow-motion, and cinematic.
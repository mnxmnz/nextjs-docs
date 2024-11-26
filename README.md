# Next.js App Router Course - Starter

## Chapter 01 - Getting Started ([Link](https://nextjs.org/learn/dashboard-app/getting-started))

## Chapter 02 - CSS Styling ([Link](https://nextjs.org/learn/dashboard-app/css-styling))

- **(Q1)** What shape do you see when using the code snippet above?
- **(A1)** [C] A black triangle
- **(Q2)** What is one benefit of using CSS modules?
- **(A2)** [B] Provide a way to make CSS classes locally scoped to components by default, reducing the risk of styling conflicts.
- **(Q3)** Search for "clsx" in your code editor, what components use it to conditionally apply class names?
- **(A3)** [A] `status.tsx` and `pagination.tsx`

## Chapter 03 - Optimizing Fonts and Images ([Link](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images))

- **(Q1)** How does Next.js optimize fonts?
- **(A1)** [D] It hosts font files with other static assets so that there are no additional network requests.
- **(Q2)** True or False: Images without dimensions and web fonts are common causes of layout shift.
- **(A2)** [A] True

### The `<Image>` Component

- Preventing layout shift automatically when images are loading.
- Resizing images to avoid shipping large images to devices with a smaller viewport.
- Lazy loading images by default (images load as they enter the viewport).
- Serving images in modern formats, like WebP and AVIF, when the browser supports it.

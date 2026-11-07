# E-Commerce Inventory & Stock Management Dashboard

Web Engineering and AI - Assignment 01 (Section A)

Name: Najaf Ali
Roll No: 241456
University: Air University Islamabad

## About

A small React dashboard to manage product stock. You can add products, change stock with the + / - buttons, delete items, filter by category or stock level, and switch between light and dark mode. Every action is saved in an audit log that stays after a page refresh.

## Run it

```
npm install
npm run dev
```

Build for production with `npm run build`.

## Folder structure

```
src/
  components/
    class/AuditLogger.jsx
    functional/ (ProductForm, ProductList, ProductCard, CardWrapper, Header, ThemeToggle, InventoryMetrics, Filters)
  context/ThemeContext.jsx
  hooks/useLocalStorage.js
  App.jsx
```

## What is used where

- Class component with lifecycle methods: `AuditLogger`
- useState: products, filters, form fields
- useEffect: saving to localStorage, document title
- useContext: theme (light / dark)
- useRef: focus on the title input
- useMemo / useCallback: filtering, metrics and handlers

## CSR vs SSR

**How do they differ?** In Client-Side Rendering (a normal Vite + React app) the server sends an almost empty HTML file and a JavaScript bundle. The browser downloads the bundle, runs React and builds the page, so the user sees a blank screen until that finishes. The server only serves static files and does no rendering work. In Server-Side Rendering (Next.js) the server runs React for every request and sends back ready-made HTML. The user sees content much earlier, and then React "hydrates" the page in the browser to make it interactive. This needs a running Node server (or serverless functions) on each request.

**Trade-offs for an e-commerce dashboard.** For performance, SSR gives a faster first paint and works better on slow phones, but the server has more load and a slower time to first byte. CSR has a heavier first load, but after that moving between pages feels very fast because nothing is fetched from the server again. For SEO, SSR is better because search engines get full HTML with product names and prices. CSR can be indexed too, but it is less reliable. For hosting, CSR is cheap and simple since the built files can sit on any static host or CDN like Netlify or GitHub Pages. SSR costs more and needs server infrastructure and scaling. This dashboard is an internal admin tool behind a login, so SEO does not matter and CSR is the better fit. For a public product catalog that customers search on Google, SSR would be the better choice.

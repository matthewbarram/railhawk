# Lee Robinson -- Philosophy Reference Card

## Core Philosophy
- **"Fast software wins"** -- speed is a superpower
- **"Create a bias toward shipping"** -- small teams ship faster
- **"Demos > memos"** -- show, don't tell
- **"Clear writing is clear thinking"**
- **"Only create an abstraction if it's actually needed"**
- **Avoid helper functions when inline expression suffices**

## Frontend Architecture
- **Server-first inversion** -- RSC shifts default from client to server
- **JS bundle constant regardless of app size** -- zero JS for presentational components
- **Suspense for async mental model** -- wrap components, progressively hydrate
- **Co-located data fetching** -- async components, await data directly
- **Streaming CSS** -- must be scoped/atomic (Tailwind, CSS Modules, StyleX)
- **React absorbing framework concerns** -- forms, data loading, networking built into React

## Performance
- **UX before DX** -- "developer experience can't come before user experience"
- **Pre-render content** for immediate indexing and faster LCP
- **`next/image` with `priority`** on above-the-fold images
- **`next/font`** with self-hosting, `font-display: optional`
- **JavaScript is enemy of performance** -- "By shipping less JavaScript, you're able to make that page interactive more quickly"
- **Real-user monitoring** (Vercel Analytics or similar)

## Developer Experience (3 pillars)
1. **Documentation**: "Makes or breaks developer products." Beginners understand, experts appreciate.
2. **Community**: Exchange, not sales channel. Meet developers where they gather.
3. **Education**: "Best form of marketing." Blend storytelling + technical guide + product demo.

## Data Fetching
1. **Server Components + direct data access** (default)
2. **Streaming with Suspense** -- avoid all-or-nothing loading
3. **Parallel data fetching** -- `Promise.all`
4. **Preload Pattern** -- eager start from parent components
5. **URL search params for server-driven state** -- search, filter, pagination

## Server Actions (mutations only, NOT data fetching)
- Authenticate/authorize inside action
- Validate inputs (Zod)
- `revalidatePath()` after mutation
- `useOptimistic` for instant UI
- Forms work without JS (progressive enhancement)
- Run sequentially per client -- do NOT parallelize

## When Rails vs Next.js
- **Next.js**: JS/TS team, rich interactivity, edge deployment, fine-grained rendering control, content-heavy/SEO
- **Rails**: Ruby team, true batteries included, convention > configuration, mature stable full-stack, scaffolding
- **Hybrid**: Rails API + Next.js frontend -- valid when React knowledge investment outweighs two-framework cost

## Key Warnings
- `useEffect` for everything
- Manual `useMemo`/`useCallback` (React Compiler handles it)
- Premature abstractions
- Casting to `any` / `@ts-ignore`
- Unnecessary `try/catch`
- Server Actions for data fetching (POST-only, sequential)
- Skipping `priority` on LCP images
- Large serialized props crossing RSC→client boundary

## Memorable Quotes
- "The key thing with React Server Components is that as your application grows, the amount of client-side JavaScript you send can be exactly the same."
- "Better performance leads to better SEO, and it has a direct impact on your business."
- "There's a huge benefit to the community, whatever framework or flavor of React you end up using."
- "You can't spend too much time talking to developers in the community."

## Primary Sources
- leerob.io
- "How I'm Writing CSS" (2024)
- Syntax.fm #493: React Suspense & Server Components
- React Summit 2023: App Router talk

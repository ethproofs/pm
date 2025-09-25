# Appendix D — Semantic Tokens & Design System

Appendix D defines Ethproofs’ semantic tokens and design system. It is the canonical reference for colors, typography, states, and component styles across both light and dark themes. By relying on Tailwind/shadcn tokens with zinc neutrals and green accents, the system avoids custom overrides while ensuring that the UI is consistent, legible, and easy to extend. Together, these tokens form the foundation of Ethproofs’ minimalist, data-first interface — guaranteeing visual coherence and reproducibility across all components and future versions.

---

## D.1 Semantic Tokens — Light vs. Dark Reference

> Tokens are the source of truth for UI surfaces. Values are shown for **Light** and **Dark** modes.

### Surfaces & Neutrals

| Token               | Light Theme           | Dark Theme            |
|---------------------|-----------------------|-----------------------|
| background          | zinc-50 `#fafafa`     | zinc-950 `#09090b`    |
| foreground          | zinc-950 `#09090b`    | zinc-50 `#fafafa`     |
| card                | zinc-50 `#fafafa`     | zinc-950 `#09090b`    |
| card-foreground     | zinc-950 `#09090b`    | zinc-50 `#fafafa`     |
| popover             | zinc-50 `#fafafa`     | zinc-950 `#09090b`    |
| popover-foreground  | zinc-950 `#09090b`    | zinc-50 `#fafafa`     |
| muted               | zinc-100 `#f4f4f5`    | zinc-800 `#27272a`    |
| muted-foreground    | zinc-600 `#52525b`    | zinc-50 `#fafafa`     |
| accent              | zinc-100 `#f4f4f5`    | zinc-800 `#27272a`    |
| accent-foreground   | zinc-950 `#09090b`    | zinc-50 `#fafafa`     |
| secondary           | zinc-200 `#e4e4e7`    | zinc-900 `#18181b`    |
| secondary-foreground| zinc-950 `#09090b`    | zinc-50 `#fafafa`     |
| border              | zinc-200 `#e4e4e7`    | zinc-700 `#3f3f46`    |
| input               | zinc-200 `#e4e4e7`    | zinc-700 `#3f3f46`    |
| ring                | zinc-400 `#a1a1aa`    | zinc-300 `#d4d4d8`    |
| placeholder         | zinc-50 `#fafafa`     | zinc-400 `#a1a1aa`    |

### Sidebar

| Token                    | Light Theme           | Dark Theme            |
|--------------------------|-----------------------|-----------------------|
| sidebar                  | zinc-100 `#f4f4f5`    | zinc-900 `#18181b`    |
| sidebar-foreground       | zinc-900 `#18181b`    | zinc-100 `#f4f4f5`    |
| sidebar-primary          | zinc-700 `#3f3f46`    | zinc-300 `#d4d4d8`    |
| sidebar-primary-foreground | zinc-50 `#fafafa`   | zinc-950 `#09090b`    |
| sidebar-accent           | zinc-200 `#e4e4e7`    | zinc-800 `#27272a`    |
| sidebar-accent-foreground| zinc-950 `#09090b`    | zinc-50 `#fafafa`     |
| sidebar-border           | zinc-200 `#e4e4e7`    | zinc-700 `#3f3f46`    |
| sidebar-ring             | zinc-400 `#a1a1aa`    | zinc-300 `#d4d4d8`    |

### Brand

| Token               | Light Theme            | Dark Theme            |
|---------------------|------------------------|-----------------------|
| primary             | green-700 `#018a34`    | green-300 `#03dc58`   |
| primary-foreground  | zinc-50 `#fafafa`      | zinc-950 `#09090b`    |
| primary-light       | green-600 `#009e3d`    | green-200 `#01f261`   |
| primary-dark        | green-800 `#00772b`    | green-500 `#01b245`   |
| primary-visited     | green-600 `#009e3d`    | green-400 `#00c74e`   |
| primary-border      | green-800 `#00772b`    | green-500 `#01b245`   |
| brand-secondary     | indigo-600 `#4f46e5`   | indigo-400 `#818cf8`  |
| brand-secondary-foreground | zinc-50 `#fafafa` | zinc-950 `#09090b`   |

### States

| Token                | Light Theme            | Dark Theme            |
|----------------------|------------------------|-----------------------|
| success              | green-600 `#16a34a`    | green-400 `#4ade80`   |
| success-foreground   | zinc-50 `#fafafa`      | zinc-50 `#fafafa`     |
| warning              | amber-600 `#d97706`    | amber-400 `#fbbf24`   |
| warning-foreground   | zinc-50 `#fafafa`      | zinc-50 `#fafafa`     |
| destructive          | red-600 `#dc2626`      | red-400 `#f87171`     |
| destructive-foreground | zinc-50 `#fafafa`    | zinc-50 `#fafafa`     |
| info                 | blue-600 `#2563eb`     | blue-400 `#60a5fa`    |
| info-foreground      | zinc-50 `#fafafa`      | zinc-50 `#fafafa`     |

### Charts

| Token        | Light Theme             | Dark Theme              |
|--------------|--------------------------|-------------------------|
| chart-1      | orange-500 `#f97316`     | orange-500 `#f97316`    |
| chart-2      | yellow-500 `#eab308`     | yellow-500 `#eab308`    |
| chart-3      | green-500 `#22c55e`      | green-500 `#22c55e`     |
| chart-4      | blue-500 `#3b82f6`       | blue-500 `#3b82f6`      |
| chart-5      | purple-500 `#a855f7`     | purple-500 `#a855f7`    |
| chart-border | zinc-200 `#e4e4e7`       | zinc-800 `#27272a`      |

---

## D.2 Typography Reference with Semantic Tokens

> Mapping of text styles to semantic tokens across desktop and mobile.

| Style       | Font Family        | Weight | Desktop Size | Mobile Size | Semantic Token        |
|-------------|--------------------|--------|--------------|-------------|-----------------------|
| Logo        | Lock Sans Stencil  | Bold   | 28–32px      | 28–32px     | `brand-primary`       |
| H1          | Lock Sans          | Light  | 96px         | 56px        | `--heading`           |
| H2          | Lock Sans          | Light  | 60px         | 48px        | `--heading`           |
| H3          | Lock Sans          | Regular| 48px         | 40px        | `--heading`           |
| H4          | Lock Sans          | Regular| 34px         | 28px        | `--heading-sub`       |
| H5          | Lock Sans          | Regular| 24px         | 20px        | `--heading-sub`       |
| H6          | Lock Sans          | Medium | 20px         | 18px        | `--heading-sub`       |
| Subtitle 1  | Lock Sans          | Regular| 16px         | 16px        | `--subtitle`          |
| Subtitle 2  | Lock Sans          | Medium | 14px         | 14px        | `--subtitle`          |
| Body 1      | Lock Sans          | Regular| 16px         | 16px        | `--body-text`         |
| Body 2      | Lock Sans          | Regular| 14px         | 14px        | `--body-muted`        |
| Button      | Lock Sans          | Medium | 14px         | 14px        | `--label-foreground`  |
| Label       | Lock Sans          | Medium | 12–14px      | 12–14px     | `--label-foreground`  |
| Caption     | Lock Sans          | Regular| 12px         | 12px        | `--caption-foreground`|
| Overline    | Lock Sans          | Regular| 10px         | 10px        | `--overline-foreground`|
| Small       | Lock Sans          | Regular| 12px         | 12px        | `--helper-foreground` |
| Badge       | Lock Sans          | Medium | 12px         | 12px        | `--label-foreground`  |
| Code        | Lock Sans          | Regular| 13px         | 13px        | `--code-foreground`   |

---

## D.3 Typography Specifications

> Authoritative list of all text styles in Ethproofs (role / family / weight / size).

- **Logo** — Lock Sans Stencil / **Bold** / 28–32px (desktop & mobile)  
- **H1** — Lock Sans / **Light** / 96px (desktop), 56px (mobile)  
- **H2** — Lock Sans / **Light** / 60px (desktop), 48px (mobile)  
- **H3** — Lock Sans / **Regular** / 48px (desktop), 40px (mobile)  
- **H4** — Lock Sans / **Regular** / 34px (desktop), 28px (mobile)  
- **H5** — Lock Sans / **Regular** / 24px (desktop), 20px (mobile)  
- **H6** — Lock Sans / **Medium** / 20px (desktop), 18px (mobile)  
- **Subtitle 1** — Lock Sans / **Regular** / 16px (desktop & mobile)  
- **Subtitle 2** — Lock Sans / **Medium** / 14px (desktop & mobile)  
- **Body 1** — Lock Sans / **Regular** / 16px (desktop & mobile)  
- **Body 2** — Lock Sans / **Regular** / 14px (desktop & mobile)  
- **Button** — Lock Sans / **Medium** / 14px (desktop & mobile)  
- **Label** — Lock Sans / **Medium** / 12–14px (desktop & mobile)  
- **Caption** — Lock Sans / **Regular** / 12px (desktop & mobile)  
- **Overline** — Lock Sans / **Regular** / 10px (desktop & mobile)  
- **Small** — Lock Sans / **Regular** / 12px (desktop & mobile)  
- **Badge** — Lock Sans / **Medium** / 12px (desktop & mobile)  
- **Code** — Lock Sans / **Regular** / 13px (desktop & mobile)  

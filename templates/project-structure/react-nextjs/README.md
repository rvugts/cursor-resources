# React Next.js Project Structure

```
project-name/
├── app/                    # Next.js 13+ App Router
│   ├── layout.tsx
│   ├── page.tsx
│   ├── globals.css
│   ├── (routes)/
│   │   ├── about/
│   │   │   └── page.tsx
│   │   └── contact/
│   │       └── page.tsx
│   └── api/
│       └── routes/
├── components/
│   ├── ui/
│   │   ├── Button.tsx
│   │   └── Input.tsx
│   ├── layout/
│   │   ├── Header.tsx
│   │   └── Footer.tsx
│   └── features/
│       └── [feature]/
├── lib/
│   ├── utils.ts
│   └── api.ts
├── hooks/
│   ├── useAuth.ts
│   └── useApi.ts
├── types/
│   └── index.ts
├── styles/
│   └── components/
├── public/
│   ├── images/
│   └── icons/
├── tests/
│   ├── __mocks__/
│   ├── components/
│   └── utils/
├── .env.local
├── .env.example
├── .gitignore
├── next.config.js
├── tsconfig.json
├── package.json
├── README.md
├── .cursor/rules
└── .cursorrules
```

## Key Directories
- `app/` - Next.js App Router pages and layouts
- `components/` - Reusable React components
- `lib/` - Utility functions and helpers
- `hooks/` - Custom React hooks
- `types/` - TypeScript type definitions
- `public/` - Static assets


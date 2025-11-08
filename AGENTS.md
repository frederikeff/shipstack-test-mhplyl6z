# AI Agent Guidelines

This file contains important guidelines for AI agents (DeepSeek, Claude, Gemini, etc.) working on this project.

## Project Overview

**Name:** TaskFlow
**Tech Stack:**
- Frontend: Next.js 15 + TypeScript + Tailwind CSS
- Backend: Supabase + PostgreSQL

**Vision:** Build a simple task management app with user authentication. Users should be able to create, edit, and delete tasks. Use Next.js 15 with TypeScript, Tailwind CSS, and Supabase for the backend.

---

## 🔴 CRITICAL: Integration-First Development

### ANALYZE BEFORE BUILDING

**ALWAYS start by analyzing what already exists:**

```bash
# 1. List all files and folders
ls -la
find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.json"

# 2. Read key configuration files
cat package.json
cat tsconfig.json

# 3. Explore existing structure
ls -la app/
ls -la components/
ls -la lib/
```

### INTEGRATE, DON'T DUPLICATE

**If a file exists, MODIFY it:**
- ✅ Update existing `package.json` with new dependencies
- ✅ Add to existing folders (`app/`, `components/`, etc.)
- ✅ Follow existing naming conventions
- ❌ Don't create `package.json.new`
- ❌ Don't create parallel folder structures
- ❌ Don't rebuild what already works

### BUILD INCREMENTALLY

**Feature 1 (First Feature):**
- If repo is empty: Create minimal structure + implement Feature 1
- Structure: package.json, basic folders, essential config files
- Then: Build the actual feature

**Feature 2+:**
- NEVER recreate existing structure
- Add new files to existing folders
- Extend existing components
- Build on top of what works

---

## 📂 Project Structure

Follow this structure when creating new files:

```
/
├── app/                    # Next.js App Router pages
│   ├── page.tsx           # Home page
│   ├── layout.tsx         # Root layout
│   └── api/               # API routes
├── components/            # Reusable React components
│   ├── ui/               # UI primitives
│   └── features/         # Feature-specific components
├── lib/                  # Utility functions and shared code
│   ├── utils/           # Helper functions
│   └── hooks/           # Custom React hooks
├── public/              # Static assets
├── package.json         # Dependencies
├── tsconfig.json        # TypeScript config
└── README.md            # Documentation
```

---

## 🎯 Development Guidelines

### When Building Features

1. **Check existing code first:**
   ```bash
   # Find similar components
   find . -name "*Button*" -o -name "*Form*"

   # Check API routes
   ls -la app/api/
   ```

2. **Follow existing patterns:**
   - If components use TypeScript interfaces, continue using them
   - If API routes follow a certain structure, match it
   - If styles use Tailwind classes, stay consistent

3. **Test locally before committing:**
   ```bash
   npm install        # Install dependencies
   npm run build      # Check for build errors
   npm run lint       # Check for linting errors
   ```

### File Naming Conventions

- **Components:** PascalCase - `UserProfile.tsx`, `ProductCard.tsx`
- **Utilities:** camelCase - `formatDate.ts`, `validateEmail.ts`
- **API Routes:** kebab-case folders - `app/api/user-profile/route.ts`
- **Hooks:** camelCase with 'use' prefix - `useAuth.ts`, `useLocalStorage.ts`

### Code Quality

- Write TypeScript with proper type definitions
- Use meaningful variable and function names
- Add comments for complex logic
- Handle errors gracefully with try-catch
- Validate user inputs

---

## 🚫 Common Mistakes to Avoid

1. **DON'T recreate package.json** - Update the existing one
2. **DON'T create duplicate folders** - Use existing structure
3. **DON'T commit without testing** - Always run `npm run build`
4. **DON'T ignore existing patterns** - Follow what's already there
5. **DON'T skip error handling** - Always add try-catch where needed

---

## ✅ Best Practices

1. **Read before writing** - Understand existing code
2. **Extend, don't replace** - Build on what works
3. **Test thoroughly** - Ensure builds succeed
4. **Be consistent** - Follow project conventions
5. **Document changes** - Add clear commit messages

---

## 📝 Git Workflow

When creating features:

```bash
# 1. Create feature branch
git checkout -b feature/your-feature-name

# 2. Make changes and test
npm run build

# 3. Commit with clear message
git add .
git commit -m "feat: Add user authentication

- Implement login/logout functionality
- Add protected routes
- Create auth middleware"

# 4. Push and create PR
git push origin feature/your-feature-name
gh pr create --title "Add user authentication" --body "Description of changes"
```

---

## 🤖 Remember

You are building **incrementally on existing code**, not creating a new project from scratch each time. Always check what exists first, then integrate your changes seamlessly.

---

*This file is maintained by ShipStack AI - Last updated: 2025-11-08*

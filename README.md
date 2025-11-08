# TaskFlow

Build a simple task management app with user authentication. Users should be able to create, edit, and delete tasks. Use Next.js 15 with TypeScript, Tailwind CSS, and Supabase for the backend.

## Vision

{
  "app_name": "TaskFlow",
  "tagline": "A streamlined task management application with secure authentication and real-time updates",
  "frontend": {
    "description": "Modern, responsive task management interface built with Next.js 15 App Router, featuring server and client components for optimal performance. Implements authentication flows, task CRUD operations, and real-time UI updates with Tailwind CSS for styling.",
    "pages": [
      "Landing Page (Public)",
      "Login Page",
      "Sign Up Page",
      "Dashboard (Protected)",
      "Task List View (Protected)",
      "Task Detail/Edit Modal (Protected)"
    ],
    "key_components": [
      "TaskCard - Individual task display with actions",
      "TaskForm - Create/edit task form with validation",
      "TaskList - Grid/list view of all tasks",
      "AuthForm - Reusable login/signup form",
      "Navbar - Navigation with user menu",
      "ProtectedRoute - Auth wrapper for protected pages",
      "TaskFilters - Filter and sort tasks",
      "DeleteConfirmModal - Confirmation dialog for deletions"
    ],
    "tech_stack": "Next.js 15 + TypeScript + Tailwind CSS",
    "reasoning": "Next.js 15 App Router provides excellent SSR/SSG capabilities with server components for auth checks and data fetching. TypeScript ensures type safety across the codebase. Tailwind CSS enables rapid UI development with utility-first approach and excellent dark mode support."
  },
  "backend": {
    "description": "Supabase-powered backend leveraging PostgreSQL for data persistence, Row Level Security for multi-tenant isolation, and built-in authentication. Next.js API routes handle business logic and Supabase client interactions.",
    "endpoints": [
      {
        "method": "POST",
        "path": "/api/tasks",
        "description": "Create a new task for authenticated user"
      },
      {
        "method": "GET",
        "path": "/api/tasks",
        "description": "Retrieve all tasks for authenticated user"
      },
      {
        "method": "PATCH",
        "path": "/api/tasks/[id]",
        "description": "Update an existing task"
      },
      {
        "method": "DELETE",
        "path": "/api/tasks/[id]",
        "description": "Delete a task"
      },
      {
        "method": "POST",
        "path": "/api/auth/signup",
        "description": "Register new user"
      },
      {
        "method": "POST",
        "path": "/api/auth/login",
        "description": "Authenticate user"
      },
      {
        "method": "POST",
        "path": "/api/auth/logout",
        "description": "End user session"
      }
    ],
    "database_schema": {
      "tables": [
        "users (managed by Supabase Auth)",
        "tasks (id, user_id, title, description, status, priority, due_date, created_at, updated_at)"
      ]
    },
    "tech_stack": "Supabase + PostgreSQL",
    "reasoning": "Supabase provides out-of-the-box authentication, real-time subscriptions, and PostgreSQL database with Row Level Security. This eliminates the need for custom auth implementation and provides automatic API generation with type-safe queries via the Supabase client."
  },
  "requirements": {
    "auth": true,
    "multi_user": true,
    "stripe": false,
    "external_apis": [],
    "custom_needs": [
      "Row Level Security policies for task isolation",
      "Email verification for new users",
      "Password reset functionality",
      "Task filtering and sorting",
      "Responsive design for mobile and desktop"
    ]
  },
  "features": [
    {
      "title": "User Authentication",
      "description": "Secure sign up, login, and logout functionality with email verification and password reset capabilities using Supabase Auth",
      "priority": 1,
      "dependencies": []
    },
    {
      "title": "Task Creation",
      "description": "Create new tasks with title, description, status, priority, and optional due date",
      "priority": 2,
      "dependencies": [
        "User Authentication"
      ]
    },
    {
      "title": "Task Listing",
      "description": "View all user tasks in a organized list/grid with sorting and filtering options",
      "priority": 2,
      "dependencies": [
        "User Authentication"
      ]
    },
    {
      "title": "Task Editing",
      "description": "Update existing tasks with inline or modal editing interface",
      "priority": 3,
      "dependencies": [
        "Task Creation",
        "Task Listing"
      ]
    },
    {
      "title": "Task Deletion",
      "description": "Delete tasks with confirmation dialog to prevent accidental removal",
      "priority": 3,
      "dependencies": [
        "Task Listing"
      ]
    },
    {
      "title": "Task Status Management",
      "description": "Toggle task status between todo, in-progress, and completed with visual indicators",
      "priority": 4,
      "dependencies": [
        "Task Creation"
      ]
    },
    {
      "title": "Task Filtering",
      "description": "Filter tasks by status, priority, and due date to focus on relevant items",
      "priority": 5,
      "dependencies": [
        "Task Listing"
      ]
    },
    {
      "title": "Responsive Design",
      "description": "Mobile-first responsive interface that works seamlessly across all device sizes",
      "priority": 4,
      "dependencies": []
    }
  ],
  "deployment": {
    "hosting": "Vercel",
    "database": "Supabase Cloud",
    "domains": [
      "taskflow.vercel.app"
    ]
  },
  "project_structure": {
    "description": "Next.js 15 App Router structure with co-located components, server actions, and type-safe API integration. Organized by feature with shared utilities and types.",
    "folders": [
      {
        "path": "app",
        "purpose": "Next.js App Router pages and layouts with nested routing"
      },
      {
        "path": "app/(auth)",
        "purpose": "Authentication pages: login, signup, reset-password"
      },
      {
        "path": "app/(dashboard)",
        "purpose": "Protected dashboard and task management pages"
      },
      {
        "path": "app/api",
        "purpose": "API route handlers for server-side operations"
      },
      {
        "path": "components",
        "purpose": "Reusable React components organized by feature"
      },
      {
        "path": "components/ui",
        "purpose": "Generic UI components (buttons, inputs, modals)"
      },
      {
        "path": "components/tasks",
        "purpose": "Task-specific components (TaskCard, TaskForm, TaskList)"
      },
      {
        "path": "lib",
        "purpose": "Utility functions and shared logic"
      },
      {
        "path": "lib/supabase",
        "purpose": "Supabase client configuration and helpers"
      },
      {
        "path": "types",
        "purpose": "TypeScript type definitions and interfaces"
      },
      {
        "path": "hooks",
        "purpose": "Custom React hooks for state and side effects"
      },
      {
        "path": "middleware",
        "purpose": "Next.js middleware for auth protection"
      }
    ],
    "initial_files": [
      {
        "path": "package.json",
        "description": "Project dependencies including Next.js 15, React 18, TypeScript, Tailwind CSS, and Supabase client"
      },
      {
        "path": "tsconfig.json",
        "description": "TypeScript configuration with strict mode enabled"
      },
      {
        "path": "tailwind.config.ts",
        "description": "Tailwind CSS configuration with custom theme and plugins"
      },
      {
        "path": "next.config.js",
        "description": "Next.js configuration for build optimization"
      },
      {
        "path": ".env.local",
        "description": "Environment variables for Supabase URL and anon key"
      },
      {
        "path": "middleware.ts",
        "description": "Auth middleware to protect routes and redirect unauthenticated users"
      },
      {
        "path": "lib/supabase/client.ts",
        "description": "Supabase client initialization for client components"
      },
      {
        "path": "lib/supabase/server.ts",
        "description": "Supabase client for server components and API routes"
      },
      {
        "path": "types/database.ts",
        "description": "Auto-generated TypeScript types from Supabase schema"
      },
      {
        "path": "types/task.ts",
        "description": "Task-related type definitions and enums"
      },
      {
        "path": "app/layout.tsx",
        "description": "Root layout with providers and global styles"
      },
      {
        "path": "app/page.tsx",
        "description": "Landing page with CTA to login/signup"
      },
      {
        "path": "components/ui/Button.tsx",
        "description": "Reusable button component with variants"
      }
    ],
    "key_patterns": [
      "Server Components for data fetching and auth checks",
      "Client Components for interactive UI with 'use client' directive",
      "Row Level Security policies in Supabase for data isolation",
      "Server Actions for mutations and form submissions",
      "Middleware-based route protection",
      "Optimistic UI updates for better UX",
      "Error boundaries for graceful error handling",
      "Type-safe database queries using generated types",
      "Separation of server and client Supabase clients",
      "Feature-based component organization"
    ]
  }
}

## Tech Stack

**Frontend:**
- Next.js 15 + TypeScript + Tailwind CSS

**Backend:**
- Supabase + PostgreSQL

## Development

This project was initialized by ShipStack AI. Features are being built incrementally by AI agents.

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

## Project Structure

This repository will be built feature-by-feature with AI assistance.

---

*Generated by [ShipStack](https://shipstack.ai) - AI-Powered Application Development*

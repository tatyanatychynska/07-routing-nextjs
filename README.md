# NoteHub

A note management application built with Next.js (App Router), featuring SSR with TanStack Query hydration, multi-page routing, and full CRUD functionality.

## Features

- Browse and search notes with debounced input
- Create notes via a modal form with validation
- Delete notes
- View individual note details
- Server-side rendering with TanStack Query prefetch and cache hydration
- Global loading and error boundaries

## Pages

| Route | Description |
|-------|-------------|
| `/` | Home page with app info |
| `/notes` | Notes list with search, pagination, create |
| `/notes/[id]` | Note detail page |

## Tech Stack

- [Next.js](https://nextjs.org) — App Router, SSR
- [TanStack Query](https://tanstack.com/query) — server state, prefetch, hydration
- [Axios](https://axios-http.com) — HTTP requests
- [Formik](https://formik.org) + [Yup](https://github.com/jquense/yup) — form and validation
- TypeScript, CSS Modules

## Getting Started

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the root:

```
NEXT_PUBLIC_NOTEHUB_TOKEN=your_token_here
```

4. Run the development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
app/
  page.tsx                        # Home page (SSR)
  layout.tsx                      # Root layout with Header, Footer, TanStackProvider
  loading.tsx                     # Global loading state
  notes/
    page.tsx                      # Notes list page (SSR + prefetch)
    Notes.client.tsx              # Client component with search/pagination logic
    error.tsx                     # Error boundary for /notes
    [id]/
      page.tsx                    # Note detail page (SSR + prefetch)
      NoteDetails.client.tsx      # Client component for note details
      error.tsx                   # Error boundary for /notes/[id]
components/
  Header/                         # Navigation header
  Footer/                         # Footer with contact info
  TanStackProvider/               # QueryClientProvider wrapper
  NoteList/                       # Notes list with delete and view details
  NoteForm/                       # Create note form
  Modal/                          # Portal-based modal
  SearchBox/                      # Search input
  Pagination/                     # Pagination control
  Loader/                         # Loading indicator
  ErrorMessage/                   # Inline error message
lib/
  api.ts                          # API functions (fetchNotes, fetchNoteById, createNote, deleteNote)
types/
  note.ts                         # Shared types (Note, NoteTag)
```

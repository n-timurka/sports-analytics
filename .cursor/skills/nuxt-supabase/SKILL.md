---
name: nuxt-supabase
description: Nuxt 3/4 + Supabase development patterns for the sports analytics UI. Use when building pages, components, composables, data fetching, auth, or GraphQL/PostgREST queries.
---

# Nuxt + Supabase Skill

## Stack conventions

- Nuxt 3/4, Vue 3 Composition API, TypeScript, pnpm
- `@nuxtjs/supabase` module
- Prefer `useSupabaseClient()` on client and server utilities as already set up in the project
- Data fetching: `useAsyncData` / `useFetch` with proper keys
- Prefer PostgREST over new server routes; use Postgres functions for complex analytics

## Patterns

```ts
// Good
const client = useSupabaseClient()
const { data, error } = await useAsyncData('standings', async () => {
  const { data, error } = await client
    .from('standings_view')
    .select('*')
    .eq('competition_id', competitionId)
  if (error) throw error
  return data
})
```

- Keep pages thin; move logic to composables (`composables/useStandings.ts` etc.).
- Components stay presentational when possible.
- Use TypeScript types generated from Supabase or hand-written shared types in `packages/`.

## Forbidden

- Introducing a separate Express/Fastify backend for CRUD
- Hard-coding Supabase keys
- Using `npm` or `yarn`

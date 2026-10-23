# Production implementation checklist

This deliverable intentionally does not claim to provide server-side security or a cloud database. Those require project credentials and deployment. Before public production launch:

1. Replace localStorage reads/writes with authenticated API/database calls.
2. Add owner login using Supabase Auth (or another established identity provider).
3. Enable and test database RLS policies. Example policy concept: public SELECT only for published products; INSERT/UPDATE/DELETE only when `auth.uid()` matches the configured owner UUID.
4. Store images in private/admin-write storage with validated uploads; use public read URLs only for published catalogue photos.
5. Add rate limiting, CSRF protections where applicable, validation, logging, and backups.
6. Add product canonical URLs, Open Graph metadata and sitemap from the real product records.
7. Confirm prices, stock, delivery/collection terms, business opening hours and all product specifications before publishing.

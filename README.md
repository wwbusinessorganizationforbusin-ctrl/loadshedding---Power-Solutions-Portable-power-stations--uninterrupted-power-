# Bright Market — power-backup catalogue storefront

A bright, responsive Marketplace-inspired single-business storefront. It uses the 221 photographs provided in `loadshedding power inverters for house.zip` (resized for web use), South African rand formatting, product search, category/availability/price filters, sorting, product detail views, favourites, a basket, and WhatsApp enquiry links to **078 741 2314**. Address displayed: **255 Nightingale Street, Mofolo South, Soweto, 1801, South Africa**.

## Run the preview

1. Extract the ZIP.
2. Open `index.html` in a modern browser, or serve this folder with a local static server (recommended):
   - Python: `python -m http.server 8000`
   - Visit `http://localhost:8000`
3. No build step is needed for the storefront preview.

## Important before publishing

This package is a working **front-end preview**, not a fully secure production e-commerce backend. Product catalogue changes in the Owner area are stored in the current browser's local storage and are not synced to customers or other devices. The Owner area is not protected by server-side authentication. Do not publish it as an administrator-secure production store or store secrets in the browser.

The uploaded archive contained product photographs but no verified product names, specifications, prices, stock levels or business name. The initial catalogue therefore uses editable placeholder names, `Price on request`, and `Confirm availability`; it does not invent commercial details. Update each product through Owner login before promoting it. The visible store name is a placeholder and can be changed in `index.html`.

## Production architecture recommended

For a real public launch, connect this storefront to **Next.js + Supabase** (Postgres, Auth and Storage) or an equivalent backend:

- Create a Supabase project and tables for `products`, `product_images`, `business_settings`, and optional promotions.
- Require Supabase Auth for the owner, enable Row Level Security (RLS), and permit catalogue writes only to the authenticated owner account. Public visitors should have read-only access to published products.
- Upload images through a server-validated route or protected storage bucket; validate MIME type and file size. Store image paths in the database, not base64 blobs in local storage.
- Move create/edit/delete/import actions into authenticated server-side endpoints and validate all submitted values.
- Add environment variables in a server-only `.env.local`; never expose a service-role key in client-side JavaScript.
- Deploy the app and backend, then set the final public URL so product enquiry messages can include a stable product link.

## Product image numbering

`assets/products/product-001.jpg` through `product-221.jpg` are the user's supplied photos. The starter catalogue pairs each image with an editable generic product record; inspect the photos and replace placeholder names/details with verified information.

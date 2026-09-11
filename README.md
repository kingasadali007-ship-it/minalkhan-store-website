# Minal Khan Store

Next.js + Supabase + Tailwind se bani e-commerce website. Domain: **minalkhan.store**. Order flow: customer cart mein products daalta hai, checkout form fill karta hai, aur ek click se WhatsApp khul jata hai jahan order details pehle se likhi hoti hain.

## Order WhatsApp numbers
- Main: **+923708939119**
- Backup: **+923223721488** (footer aur order-success page par dikhta hai)

## 1. Supabase setup

1. Supabase project already ban chuka hai. Dashboard -> **SQL Editor** kholein.
2. `supabase/schema.sql` file ka poora content paste karke **Run** karein. Ye `products` aur `orders` tables banayega, security policies set karega, aur 4 sample products daal dega.
3. Apne asal products add karne ke liye: Dashboard -> **Table Editor** -> `products` table -> row add karein. `image_url` mein Supabase Storage ya kisi bhi public image link daal sakte hain.

## 2. Local setup (apne computer par test karne ke liye)

```bash
npm install
cp .env.local.example .env.local
npm run dev
```

Phir browser mein `http://localhost:3000` kholein.

## 3. Vercel par deploy karna

1. Is folder ko GitHub repo mein push karein (ya Vercel CLI se seedha deploy karein: `vercel`).
2. Vercel dashboard -> **New Project** -> apna repo import karein.
3. **Environment Variables** mein ye do add karein (values `.env.local.example` mein maujood hain):
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`
4. **Deploy** dabayein.
5. Deploy hone ke baad, Vercel Project Settings -> **Domains** mein `minalkhan.store` add karein aur DNS records apne domain registrar (jahan se `.store` domain khareeda hai) mein daal dein — Vercel ye records deploy ke waqt khud dikha dega.

## Project structure

```
app/                Pages (home, products, product detail, cart, order-success)
components/         Header, Footer, ProductCard, AddToCartForm, CheckoutForm
lib/                Supabase client, cart logic (localStorage), WhatsApp message builder
supabase/schema.sql Database tables + sample products
```

## Products data kahan se aa rahi hai

Agar Supabase `products` table khaali ho ya connect na ho paaye, site khud-ba-khud 4 sample/dummy products dikha degi taake site kabhi khaali na lage. Jaise hi aap Supabase mein asal products add karenge, wahi show hone lagenge.

## Aage kya customize kar sakte hain

- Colors/fonts: `tailwind.config.js`
- Homepage hero text: `app/page.tsx`
- WhatsApp message ka format: `lib/whatsapp.ts`
- Naye pages (About, Contact, etc.): `app/` folder mein naya folder banayein

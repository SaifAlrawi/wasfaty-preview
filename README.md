# Wasfaty preview

The compiled Wasfaty web app, published so it can be opened in a browser
and clicked through. **Built output only — no source code lives here.**

Live at https://saifalrawi.github.io/wasfaty-preview/

The app talks to Supabase with the public anon key, which is what every
deployed web app ships and is safe by design: it grants nothing on its
own. Every row is still fenced by row-level security, and every screen
still requires signing in.

Source, history and issues live in the private Wasfaty repository.

# OFFLUST

Site estático (HTML + JS) com conta opcional e base de dados Supabase. Sem conta, tudo fica no aparelho.

## 1. Supabase
1. Cria um projeto em supabase.com.
2. SQL Editor → cola o conteúdo de `supabase/schema.sql` → Run.
3. Project Settings → API → copia o **Project URL** e a **anon/publishable key** para `config.js`.
   (Nunca uses a `service_role` key. A anon key é pública e é protegida pelas regras RLS do schema.)
4. Authentication → Providers → Email: deixa ativo. Para testar mais depressa podes desligar "Confirm email".

## 2. GitHub
Envia esta pasta para um repositório (index.html, config.js, vercel.json, supabase/).

## 3. Vercel
1. vercel.com → Add New → Project → importa o repositório.
2. Framework Preset: **Other**. Sem build command, sem output directory.
3. Deploy.

## 4. Voltar ao Supabase
Authentication → URL Configuration → **Site URL** = o endereço da Vercel (ex.: https://offlust.vercel.app).
Adiciona também esse endereço em Redirect URLs.

Pronto: Perfil → Conta → Criar conta / Entrar.

## Notas
- Os dados ficam numa tabela `app_state` (um JSON por utilizador), visíveis só para o próprio utilizador.
- Não têm encriptação de ponta a ponta: o administrador do projeto Supabase consegue lê-los.

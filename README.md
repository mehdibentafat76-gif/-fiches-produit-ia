# Prêt à vendre — fiches produit IA

Générateur de fiches produit (3 tons, en français) pour vendeurs Etsy/Shopify/marketplace, propulsé par l'API Claude.

## 1. Tester en local

```bash
npm install
echo "ANTHROPIC_API_KEY=ta_cle_ici" > .env.local
npm run dev
```

Récupère ta clé API sur https://console.anthropic.com (section "API Keys"). Sans backend local pour `/api/generate`, le bouton "Générer" ne fonctionnera qu'une fois déployé sur Vercel (étape 2) — Vercel exécute automatiquement le dossier `api/` comme des fonctions serverless.

## 2. Déployer sur Vercel (gratuit)

1. Crée un compte sur https://vercel.com (connexion avec GitHub)
2. Crée un repo GitHub et pousse ce dossier dedans :
   ```bash
   git init
   git add .
   git commit -m "premier déploiement"
   git remote add origin https://github.com/TON-COMPTE/fiches-produit-ia.git
   git push -u origin main
   ```
3. Sur Vercel : "Add New Project" → importe le repo
4. Dans "Environment Variables", ajoute `ANTHROPIC_API_KEY` avec ta clé
5. Clique "Deploy" → tu obtiens une URL du type `fiches-produit-ia.vercel.app`

Chaque futur `git push` redéploie automatiquement.

## 3. Nom de domaine (optionnel)

Dans Vercel → Settings → Domains, tu peux brancher un nom de domaine acheté ailleurs (Namecheap, OVH...) en quelques clics.

## 4. Monétiser simplement, sans coder de système de paiement

L'option la plus rapide : un **Stripe Payment Link**.

1. Crée un compte sur https://dashboard.stripe.com
2. Va dans "Payment Links" → crée un lien pour un abonnement mensuel (ex. 9€/mois)
3. Colle ce lien sur un bouton "Devenir membre" sur ton site, ou envoie-le directement aux personnes intéressées après leur test gratuit

Pour cette première version, le plus simple est de garder l'outil en accès libre, et de gérer l'accès "payant" manuellement (tu donnes l'URL après paiement). Construire un vrai système de comptes/abonnements est une étape utile, mais seulement une fois que tu as confirmé que des gens paient.

## Limites connues de cette V1

- Pas de compte utilisateur : les fiches "gardées" sont stockées dans le navigateur de chaque visiteur (localStorage), pas sur un serveur partagé
- Pas de limite de génération : si tu mets le site en public, surveille ta consommation d'API sur console.anthropic.com pour éviter une facture surprise
- Pas encore de blocage d'accès derrière un paiement

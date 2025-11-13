# CRM Frontend Vue (Vite + Vue 3 + Pinia + Axios)

Un starter minimaliste et prêt à l’emploi pour construire une application Vue 3 avec Pinia et Axios, propulsé par Vite.

## Prérequis

- Node.js >= 18

## Installation

```bash
npm install
```

## Démarrage en dev

```bash
npm run dev
```

## Build de production

```bash
npm run build
```

## Preview de la build

```bash
npm run preview
```

## Configuration API

Copiez `env.example` en `.env` (ou `.env.local`) et ajustez la variable:

```
VITE_API_BASE_URL=http://localhost:3000/api
```

## Structure

- `src/main.ts`: bootstrap de l’appli, Pinia inclus
- `src/App.vue`: composant racine avec compteur et test API `/me`
- `src/stores/counter.ts`: store Pinia d’exemple
- `src/services/http.ts`: instance Axios avec interceptors et baseURL
- `src/services/userService.ts`: service d’exemple

## Notes

- Les tokens d’accès JWT (si utilisés) sont lus depuis `localStorage` (`access_token`).
- Adaptez la gestion d’erreurs globale dans `src/services/http.ts` selon vos besoins.

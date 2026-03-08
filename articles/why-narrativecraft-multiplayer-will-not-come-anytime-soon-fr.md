---
Date: 2026-03-02 22:31
Draft: true
Layout: post
Summary: narrativecraft next update is slow, and i explain why
Title: why narrativecraft multiplayer will not come anytime soon
---

[english](/p/why-narrativecraft-multiplayer-will-not-come-anytime-soon)

depuis novembre 2025, narrativecraft n’a reçu aucune mise à jour. voici pourquoi.

narrativecraft est un mod minecraft qui compte beaucoup pour moi. je travaille dessus depuis 11 mois.

## comment narrativecraft a évolué

le modding minecraft est difficile, surtout en partant de zéro. en avril 2025, j’ai commencé avec de petits projets pour apprendre. il n’existe pas d’api simple et prête à l’emploi. il faut explorer, lire le code source de minecraft et comprendre à la fois le client et le serveur.

au début, je ne comprenais pas l’importance de bien séparer la logique client et serveur.

une fois suffisamment formé, j’ai lancé narrativecraft, mon plus grand projet à ce jour.

## commencer trop grand avec peu d’expérience

j’ai développé narrativecraft tout en continuant à apprendre. le projet est devenu un terrain d’expérimentation sans feuille de route claire. les fonctionnalités étaient ajoutées de manière désorganisée.

une version bêta a été publiée et bien accueillie, mais en interne le mod était instable, mal structuré et sujet à de nombreux crashs.

corriger les bugs ne suffisait pas. la structure était problématique. j’ai donc décidé de tout réécrire.

## première réécriture

j’ai entièrement réécrit le projet pendant un mois et publié la version 1.0.0.

elle était plus stable, mais souffrait encore d’une architecture fragile et de bugs difficiles à reproduire. après sa sortie et une [vidéo youtube](https://www.youtube.com/watch?v=8J2jwnHP7c) expliquant le développement, j’ai voulu ajouter la fonctionnalité la plus demandée : le multijoueur.

## le problème du multijoueur

au départ, je n’avais pas correctement implémenté les packets ni la communication client-serveur. le mod fonctionnait en solo, mais ne chargeait pas sur serveur ou provoquait des crashs.

pour supporter le multijoueur, il fallait mettre en place un système de packets. j’ai commencé en janvier 2026. des progrès ont été faits, mais la motivation a chuté. travailler exclusivement sur ce projet a conduit à un début de burnout.

de plus, la base de code était devenue difficile à maintenir. la relire était démotivant. j’ai donc pris la décision de recommencer une seconde fois.

## seconde réécriture

le code actuel est trop instable et mal structuré pour évoluer correctement. ajouter le multijoueur et maintenir la compatibilité entre versions est devenu trop complexe.

avec l’expérience acquise, je sais désormais précisément comment reconstruire narrativecraft avec un support multijoueur propre et une architecture maintenable.

cette réécriture prendra plusieurs mois. aucune date de sortie ne peut être annoncée.

je travaille toujours sur le mod. l’objectif est de proposer une version stable, avec un code propre et un multijoueur fiable.

pour soutenir le projet, vous pouvez faire un don sur ko-fi :
https://ko-fi.com/loudo

des devlogs sont prévus, je les écriraient quand ça sera possible

pour l’instant, attendez.

a++ :p
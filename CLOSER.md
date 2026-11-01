# Profil closer : alternative à l'affiliateur

Proposition du 2026-11-01. **À valider** : les valeurs marquées ⚙️ sont des choix par défaut, réglables par l'admin comme ceux de l'affiliateur.

Ce document complète `AFFILIATION.md`. Tout ce qui n'est pas redéfini ici (calcul de la base, remboursements, versements manuels, accès par code) reste identique.

## Différence avec l'affiliateur

| | Affiliateur | Closer |
|---|---|---|
| Rôle | Recommande COSMO, le client s'inscrit seul par le lien | **Vend activement** : prospecte, fait la démo, conclut la vente |
| Cible | Particuliers et organisations | **Organisations** surtout (abonnements Entreprise), particuliers acceptés |
| Attribution | Lien `?aff=`, dernier clic gagne, 30 jours | Lien personnel **ou** rattachement manuel par l'admin après la vente (deal conclu par appel, sans clic) |
| Durée de commission | À vie | ⚙️ **12 premiers mois** de paiements du client |
| Taux | 50 % de la base | ⚙️ **50 % de la base** pendant 12 mois, puis 0 |
| Retenue | 14 jours | ⚙️ **30 jours** (laisse passer les 14 jours de rétractation et le premier mois d'usage) |
| Prime | Aucune | ⚙️ Prime de signature optionnelle, fixe, saisie à la main par l'admin |

**Pourquoi limiter à 12 mois** : un closer est payé pour la vente, pas pour la fidélité du client. Une commission à vie sur des organisations, qui paient plus cher et plus longtemps, coûterait plus que la valeur de la vente. 12 mois à 50 % équivaut à environ 6 mois de net encaissé : c'est dans la fourchette habituelle des closers en SaaS.

## Règles de rémunération

- **Base** : identique à l'affiliateur : `payé HT − 25,6 % du payé − frais Stripe estimés`.
- **Commission** : `base × 50 %` sur chaque paiement reçu **pendant les 12 mois** qui suivent le premier paiement du client. Un annuel payé d'avance est commissionné en une fois, au paiement, pour les 12 mois.
- **Après 12 mois** : plus de commission. Le client reste rattaché au closer (historique, statistiques), mais ne lui rapporte plus rien.
- **Retenue** : une commission devient versable **30 jours** après le paiement.
- **Remboursement** (rétractation ou exception légale) : commission négative au prorata, déduite tout de suite, comme pour l'affiliateur.
- **Résiliation** pendant les 12 mois : les commissions déjà acquises restent dues ; les paiements suivants n'existent plus, donc pas de commission.
- **Prime de signature** (optionnelle) : montant fixe par organisation signée, enregistré à la main par l'admin, soumis à la même retenue de 30 jours. Elle est annulée si le client se rétracte.
- **Taux figés par ligne** : un changement de réglage ne recalcule pas le passé.

**Exemple** : une organisation paie 49 €/mois.
- Base = 49 − 12,54 − 0,99 = 35,47 € → commission **17,74 €/mois**.
- Sur 12 mois : **212,88 €**, puis plus rien.
- En annuel payé d'avance (490 €) : base = 490 − 125,44 − 7,60 = 356,96 € → **178,48 €** en une fois.

## Attribution

1. **Lien personnel** `?aff=<slug>` : mêmes règles que l'affiliateur (dernier clic, 30 jours, définitif).
2. **Rattachement manuel** par l'admin, après une vente conclue hors lien, avec l'email du compte ou de l'organisation. Seuls les paiements postérieurs au rattachement comptent.
3. **Conflit** : si le client était déjà rattaché à un affiliateur, le closer **ne le récupère pas** (le rattachement est définitif). L'admin peut décider d'une prime de signature pour compenser.

## Ce que voit le closer (pages cosmo-analytics)

Mêmes écrans que l'affiliateur, avec en plus :
- **Fin de commission** de chaque client : date à laquelle les 12 mois se terminent ;
- **Commissions à venir** : estimation de ce que rapportent encore les clients actifs avant la fin de leurs 12 mois ;
- **Primes de signature** : liste et total ;
- **En attente** (30 jours), **reste à payer**, **versé**.

## Statut juridique et contrat

- Le closer est un **prestataire indépendant** (micro-entreprise ou société), pas un salarié. Il facture COSMO pour chaque versement. S'il travaille à plein temps pour COSMO seul, avec des horaires et des objectifs imposés, il y a un risque de requalification en contrat de travail : le contrat ne doit pas prévoir de lien de subordination.
- Le contrat précise : la durée de 12 mois, la retenue de 30 jours, la reprise des commissions remboursées et leur compensation sur les gains futurs, la prime éventuelle, la confidentialité des données clients, et l'interdiction de promettre des conditions que COSMO ne propose pas (remise, remboursement, fonctionnalité).
- **Démarchage** : le closer doit respecter les règles de prospection. Par téléphone vers des particuliers, il doit vérifier la liste Bloctel. Par email vers des professionnels, il doit utiliser une adresse professionnelle en lien avec l'offre et proposer un lien de désinscription.
- Une vente conclue par téléphone avec un **particulier** reste une vente à distance : 14 jours de rétractation et confirmation écrite obligatoires.

## Guide du closer : tout savoir sur la facturation

Cette partie est écrite pour le closer lui-même, sans jargon. Elle lui permet de répondre à toutes les questions d'un client sur les prix, le paiement et les remboursements. **Il ne doit rien promettre d'autre que ce qui est écrit ici.**

### Les offres

**Usage personnel : gratuit.**
Tâches, habitudes, agenda, objectifs (OKR), statistiques et partage : tout est gratuit pour un particulier, sans carte bancaire et sans limite de durée.

**Organisations (entreprises, associations, équipes) : gratuit jusqu'à 5 membres, puis un forfait selon le nombre de membres.**

| Nombre de membres | Mensuel | Annuel (−25 %) |
|---|---|---|
| Jusqu'à 5 | Gratuit | Gratuit |
| 6 à 10 | 70 € / mois | 52,50 € / mois, soit 630 € par an |
| 11 à 20 | 150 € / mois | 112,50 € / mois, soit 1 350 € par an |
| 21 à 50 | 350 € / mois | 262,50 € / mois, soit 3 150 € par an |
| 51 à 100 | 700 € / mois | 525 € / mois, soit 6 300 € par an |
| Plus de 100 | 1 000 € / mois | 750 € / mois, soit 9 000 € par an |

- Le prix couvre **toute l'organisation** : projets, équipes et objectifs illimités. Aucun module à débloquer, aucun devis.
- **Toutes les fonctionnalités sont incluses dans tous les paliers**, gratuit compris. On paie pour le nombre de personnes, pas pour des options.
- Chaque membre garde **son espace personnel**, avec son compte habituel. Ses tâches et habitudes personnelles ne sont jamais visibles par son manager.

### Questions fréquentes des clients

**« Les prix sont HT ou TTC ? »**
Les prix affichés sont ceux que le client paie. COSMO n'applique pas de TVA aujourd'hui (franchise de TVA) : il n'y a rien à ajouter.

**« Comment on paie ? »**
En ligne, au moment de choisir le forfait, par carte bancaire. Le paiement est géré par Stripe, un prestataire de paiement sécurisé : COSMO ne voit jamais les numéros de carte.

**« Est-ce que je reçois une facture ? »**
Oui, un reçu est envoyé par email à chaque paiement. Pour toute demande particulière (nom de société, adresse de facturation, copie), écrire à contact@thecosmo.app.

**« Mensuel ou annuel, quelle différence ? »**
- **Mensuel** : payé chaque mois, sans engagement, résiliable à tout moment.
- **Annuel** : 25 % moins cher, payé en une fois pour 12 mois. Renouvelé automatiquement chaque année, sauf résiliation. Le client reçoit un email **45 jours avant** chaque renouvellement pour le lui rappeler.

**« Et si notre équipe grandit ? »**
Quand l'organisation atteint la limite de son palier, elle ne peut plus inviter de nouveau membre tant qu'elle n'est pas passée au palier suivant. **Personne n'est jamais retiré** en attendant.

**« Et si notre équipe diminue ? »**
Le forfait peut redescendre au palier correspondant. Rien n'est perdu.

**« Peut-on essayer avant de payer ? »**
Oui : jusqu'à 5 membres, c'est gratuit et complet, sans carte bancaire. Pour une équipe plus grande, on peut commencer à 5 pour tester, puis passer au palier payant.

**« Comment résilier ? »**
Depuis la page **Facturation** de l'organisation, en quelques clics, sans appeler personne. L'accès continue jusqu'à la fin de la période déjà payée, puis l'organisation repasse en gratuit (5 membres). **Aucune donnée n'est supprimée** par la résiliation.

**« Peut-on être remboursé ? »**
- **Particulier, ou très petite entreprise (5 salariés ou moins) qui achète hors de son métier** : 14 jours pour changer d'avis après la souscription, avec le bouton « Se rétracter » de la page Facturation. On lui rembourse la part de la période qu'il n'a pas utilisée, sous 14 jours, sur la même carte.
- **Après 14 jours** : pas de remboursement, ni en mensuel ni en annuel. Le client peut résilier, et il garde l'accès jusqu'à la fin de ce qu'il a payé.
- **Exceptions** : si le service ne fonctionne pas comme promis, si COSMO change ses prix ou ses conditions, ou si le rappel de renouvellement n'a pas été envoyé, le client peut obtenir un remboursement. Il écrit alors à contact@thecosmo.app.
- **Autres entreprises** : pas de droit de rétractation, pas de remboursement, sauf si le service ne fonctionne pas.

**« Les prix peuvent-ils augmenter ? »**
Si COSMO change ses prix, le client est prévenu par email **au moins un mois avant**, et il peut résilier sans frais avant l'entrée en vigueur.

**« Où sont stockées nos données ? »**
En Europe (Irlande), sur des serveurs sécurisés. Elles ne sont jamais revendues. La suppression d'un compte ou d'une organisation est réelle et se fait en quelques clics.

**« Qui contacter en cas de problème de paiement ? »**
contact@thecosmo.app. Si un paiement échoue, l'abonnement passe en « paiement en échec » : le client doit mettre sa carte à jour depuis la page Facturation.

### Ce que le closer ne doit jamais faire

- Promettre une **remise**, un **mois offert**, un **remboursement** ou une **fonctionnalité** qui n'existe pas. Seul l'admin de COSMO peut accorder un geste commercial, par écrit.
- Saisir lui-même les **coordonnées bancaires** du client, ou les lui demander par téléphone ou par email. Le client paie toujours lui-même, en ligne.
- Dire qu'un abonnement annuel est remboursable « à tout moment ».
- Faire signer quoi que ce soit au nom de COSMO.
- En cas de doute : « Je vérifie et je reviens vers vous », puis écrire à contact@thecosmo.app.

### Ce que le closer doit savoir sur sa propre rémunération

- Il touche **50 % de ce qui reste** du paiement du client, après avoir retiré 25,6 % du montant et les frais du prestataire de paiement (environ 1,5 % + 0,25 €).
- Pendant les **12 premiers mois** de paiements de chaque client qu'il a amené. Ensuite, plus rien sur ce client.
- Une commission devient versable **30 jours** après le paiement du client.
- Si le client est **remboursé**, la commission correspondante est retirée, même si elle a déjà été versée. Elle est alors déduite des commissions suivantes.
- Si le client **résilie**, ce qui a déjà été gagné reste acquis.
- **Les organisations gratuites (5 membres ou moins) ne rapportent rien** tant qu'elles ne passent pas à un palier payant. Son intérêt est donc de viser les équipes de plus de 5 personnes.
- Ce qui rapporte le plus : les **grandes équipes** et l'**annuel**, payé d'avance et commissionné en une fois.

| Le client choisit | Le closer touche |
|---|---|
| 6 à 10 membres, mensuel (70 €) | 25,39 € par mois pendant 12 mois, soit 304,68 € |
| 6 à 10 membres, annuel (630 €) | 229,51 € en une fois |
| 11 à 20 membres, mensuel (150 €) | 54,55 € par mois, soit 654,60 € sur 12 mois |
| 21 à 50 membres, annuel (3 150 €) | 1 148,05 € en une fois |

Les versements se font par virement. Le closer envoie une facture à COSMO pour chaque versement.

## Implémentation (COSMO + cosmo-analytics)

- `affiliates` : nouvelle colonne `kind` (`'affiliate' | 'closer'`, défaut `'affiliate'`).
- `affiliate_settings` : réglages par type, ou une table `affiliate_kind_settings` (`kind`, `commission_bp`, `duration_months`, `hold_days`). Valeurs closer : 5000 / 12 / 30. Affiliateur : 5000 / NULL (à vie) / 14.
- `affiliate_process()` : pour un closer, ne commissionne que les paiements dont `occurred_at` tombe dans les `duration_months` qui suivent le premier paiement commissionné du client.
- `affiliate_bonuses` (`id`, `affiliate_id`, `customer_id` ou `org_id`, `amount_cents`, `occurred_at`, `note`) pour les primes, comptées dans le revenu et soumises à la retenue.
- API : `kind` dans la création et le profil, `hold_days` lu par type pour « en attente », routes pour les primes (admin).
- cosmo-analytics : choix du type à la création, colonnes « Fin de commission » et « Commissions à venir », réglages par type.

## Points à valider

1. Durée de 12 mois et taux de 50 % pour le closer ?
2. Retenue de 30 jours ou 14 jours comme l'affiliateur ?
3. Prime de signature : oui ou non, et quel montant par défaut ?
4. Un closer peut-il aussi vendre aux particuliers ?

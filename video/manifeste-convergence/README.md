# Manifeste — Intelligence de Convergence®

Vidéo LinkedIn carrée (1080×1080, 46 s, sans son) produite avec
[OpenMontage](https://github.com/calesthio/OpenMontage) (commit `195eab2`),
moteur de montage Remotion, aux couleurs du Mémo 360° CSMCI Groupe.

| Fichier | Rôle |
|---|---|
| `manifeste-convergence-1x1.mp4` | La vidéo finale |
| `convergence-manifeste.json` | Le storyboard : textes, durées, couleurs (modifiable) |
| `openmontage-fixes.patch` | Corrections apportées aux composants d'OpenMontage |

## Déroulé

1. 0–4 s — « Vos décisions ont des angles morts. »
2. 4–20,5 s — trois chiffres sourcés (voir ci-dessous)
3. 20,5–30 s — « Le problème n'est pas l'information. C'est qu'elle arrive en silos. » / « Valeur. Finances. Conformité. »
4. 30–35,5 s — Intelligence de Convergence® : *faire converger toutes les dimensions d'un projet pour révéler les angles morts avant de décider.*
5. 35,5–40 s — « Lancer. Ajuster. Repenser. Décider en voyant tout. »
6. 40–46 s — Signature CSMCI Groupe

## Sources des chiffres

- **47 %** des dirigeants finance et tech ont pris une décision majeure sur des données inexactes, incomplètes ou périmées en un an — enquête OneStream (350+ dirigeants, É.-U./R.-U.), rapportée par [CFO Dive, 12 mai 2026](https://www.cfodive.com/news/execs-admit-material-decisions-based-flawed-data/819927/).
- **38 %** des dirigeants de l'assurance ne sont pas sûrs d'avoir une vue d'ensemble en temps réel de leurs risques, revenus et coûts — [SAS / Risk.net, *Breaking Silos*, 13 nov. 2025](https://www.sas.com/en_za/news/press-releases/2025/november/insurance-survey-silos.html).
- **54 %** des dirigeants ne sont pas pleinement sûrs de savoir trouver, analyser et interpréter leurs données — [Salesforce, 15 avr. 2025](https://www.salesforce.com/news/stories/trust-in-business-data-leaders-survey/) (552 dirigeants, É.-U.).

OneStream et Salesforce sont des éditeurs qui commandent ces enquêtes ; le chiffre SAS ne concerne que le secteur de l'assurance.

## Re-générer la vidéo

```bash
git clone https://github.com/calesthio/OpenMontage.git && cd OpenMontage
git checkout 195eab2
make setup
git apply /chemin/vers/openmontage-fixes.patch
cp /chemin/vers/convergence-manifeste.json remotion-composer/public/demo-props/
cd remotion-composer
npx remotion render src/index.tsx Explainer manifeste.mp4 \
  --props public/demo-props/convergence-manifeste.json \
  --codec h264 --width=1080 --height=1080
```

Pour une version verticale 9:16, remplacer par `--width=1080 --height=1920`.

## Corrections incluses dans le patch

- `HeroTitle.tsx` : les titres ne se coupent plus au milieu des mots, et la couleur d'accent porte bien sur le premier mot (et non sur les 8 premiers caractères).
- `StatCard.tsx` : marge latérale et interligne pour le texte sous les chiffres (lisibilité en format carré ou vertical).

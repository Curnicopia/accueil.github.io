![Atrium logo](Atrium.png)

# Atrium — Dashboard de tuiles / Tile Dashboard

![Atrium screenshot](capture.png)

> Page d’accueil personnelle en un seul fichier HTML/CSS/JS.  
> Personal start page in a single HTML/CSS/JS file.

---

## 🇬🇧 English

### Overview

Atrium is a self-contained, single-file dashboard that lets you organize your favourite links, apps, and shortcuts as draggable tiles inside resizable categories and tabs. It runs entirely in the browser: no build step, no server, no external dependencies except the fonts loaded from Google Fonts.

### Features

#### Tabs
- Create multiple tabs to separate contexts (work, personal, projects, etc.).
- Rename any tab by clicking its edit icon or double-clicking the label.
- Delete a tab; its categories and tiles are removed with a confirmation prompt.
- Each tab owns its own set of categories and tiles.

#### Categories
- Add new categories inside the current tab.
- Rename or delete a category from its header.
- Drag a category by its handle to reorder it vertically.
- Resize a category horizontally with the resize handle on its right edge.
- Auto-fit the category width to its content.

#### Tiles
- Add a tile with a name, URL, and category.
- Edit a tile to change its label, link, category, or icon.
- Delete a tile.
- Click a tile to open its URL in a new tab.

#### Drag & drop
- Drag a tile to move it inside the same category or to another category.
- Drop a tile directly onto another tile to **swap their positions**.
- Drag uses a custom ghost preview and a pointing-finger cursor.

#### Icons
- If no custom image is uploaded, the tile automatically fetches the target site’s favicon.
- Upload a custom image (PNG, JPG, etc.); it is embedded as base64 inside the page data so it is preserved on export.

#### Wallpaper & appearance
- Upload a custom background image.
- Choose from preset colour gradients.
- The UI uses a glassmorphism style: translucent panels, blur, subtle borders, and a dark theme.

#### Clock
- Large centred clock at the top of the page.
- Displays the full date below the time.

#### Language
- Switch between **French** and **English** with the language button in the header.
- All labels, placeholders, and confirmation messages are translated.

#### Export & import
- **Export** button (bottom-right) downloads a `.json` backup containing:
  - tabs, categories, and tiles;
  - custom tile icons;
  - wallpaper image;
  - current language and layout.
- **Import** button reloads a previously exported file after confirmation.
- This makes it easy to move your dashboard from one computer to another.

#### Data safety
- All data is stored in the browser’s `localStorage` under the key `dashboard-tuiles-data-v1`.
- On every save, a secondary copy is written to `dashboard-tuiles-data-v1-backup`.
- On startup, if the main data is missing or corrupt, the page tries to recover from:
  - the automatic backup;
  - any older key names that may still exist in the browser.
- Corrupt data is kept aside (key suffixed with `-corrupt-<timestamp>`) instead of being erased.

### How to use

1. Open `index.html` in any modern browser.
2. Create tabs, categories, and tiles.
3. Drag tiles and categories to organise your dashboard.
4. Click **Export** regularly to keep a safe backup on your computer.
5. To move to another machine, copy the exported `.json` file and click **Import** there.

### Deployment

Simply upload `index.html` to any static host (GitHub Pages, Netlify, Vercel, Apache/Nginx, etc.). No build step is required.

### Backup file format

The exported file is a JSON object with the following structure:

```json
{
  "app": "dashboard-tuiles",
  "version": 1,
  "exportedAt": "2026-09-07T08:41:00.000Z",
  "data": {
    "tabs": [...],
    "categories": [...],
    "tiles": [...],
    "wallpaper": "data:image/...",
    "lang": "fr",
    "hoverColor": "#4f8ff7"
  }
}
```

Because images are embedded as base64 strings, the backup file is self-contained and can be copied to another computer without any extra assets.

### Browser compatibility

- Chrome / Edge / Firefox / Safari (recent versions).
- Requires JavaScript and `localStorage`.

### Notes

- Data lives in the browser profile used to open the page. If you open the same file from a different URL (`http` vs `https`, `www` vs bare domain, or a `file://` path), the browser may use a separate storage bucket.
- Clear browsing data / localStorage will delete your dashboard. Use **Export** to keep backups.

---

## 🇫🇷 Français

### Présentation

Atrium est un tableau de bord personnel contenu dans un seul fichier HTML/CSS/JS. Il permet d’organiser ses liens, applications et raccourcis favoris sous forme de tuiles déplaçables, regroupées dans des catégories redimensionnables et des onglets. Aucune compilation, aucun serveur, aucune dépendance externe n’est requise, hormis les polices chargées depuis Google Fonts.

### Fonctionnalités

#### Onglets
- Créer plusieurs onglets pour séparer différents contextes (travail, personnel, projets, etc.).
- Renommer un onglet via son icône d’édition ou en double-cliquant sur son libellé.
- Supprimer un onglet ; ses catégories et tuiles sont effacées avec une demande de confirmation.
- Chaque onglet possède son propre ensemble de catégories et de tuiles.

#### Catégories
- Ajouter une nouvelle catégorie dans l’onglet actif.
- Renommer ou supprimer une catégorie depuis son en-tête.
- Déplacer une catégorie verticalement en la saisissant par sa poignée.
- Redimensionner une catégorie horizontalement avec la poignée située sur son bord droit.
- Ajuster automatiquement la largeur d’une catégorie à son contenu.

#### Tuiles
- Ajouter une tuile avec un nom, une URL et une catégorie.
- Modifier une tuile pour changer son libellé, son lien, sa catégorie ou son icône.
- Supprimer une tuile.
- Cliquer sur une tuile pour ouvrir son URL dans un nouvel onglet.

#### Glisser-déposer
- Déplacer une tuile au sein d’une même catégorie ou vers une autre catégorie.
- Lâcher une tuile directement sur une autre tuile pour **échanger leurs positions**.
- Le glisser-déposer utilise un aperçu fantôme personnalisé et un curseur en forme de doigt pointé.

#### Icônes
- En l’absence d’image personnalisée, la tuile récupère automatiquement le favicon du site cible.
- Possibilité de téléverser une image personnalisée (PNG, JPG, etc.) ; celle-ci est intégrée en base64 dans les données de la page et donc conservée lors de l’export.

#### Fond d’écran et apparence
- Téléversement d’une image de fond personnalisée.
- Choix parmi des dégradés de couleurs prédéfinis.
- Interface en glassmorphism : panneaux translucides, flou, bordures subtiles et thème sombre.

#### Horloge
- Grande horloge centrée en haut de la page.
- Affichage de la date complète sous l’heure.

#### Langue
- Bascule entre le **français** et l’**anglais** grâce au bouton de langue dans l’en-tête.
- Tous les libellés, placeholders et messages de confirmation sont traduits.

#### Export et import
- Le bouton **Exporter** (en bas à droite) télécharge un fichier `.json` de sauvegarde contenant :
  - les onglets, catégories et tuiles ;
  - les icônes personnalisées des tuiles ;
  - l’image de fond d’écran ;
  - la langue active et la disposition.
- Le bouton **Importer** recharge un fichier précédemment exporté après confirmation.
- Cela permet de transférer facilement son tableau de bord d’un ordinateur à un autre.

#### Sécurité des données
- Toutes les données sont stockées dans le `localStorage` du navigateur, sous la clé `dashboard-tuiles-data-v1`.
- À chaque enregistrement, une copie secondaire est écrite sous la clé `dashboard-tuiles-data-v1-backup`.
- Au démarrage, si les données principales sont manquantes ou corrompues, la page tente de récupérer :
  - la sauvegarde automatique ;
  - d’éventuelles anciennes clés encore présentes dans le navigateur.
- Les données corrompues sont mises de côté (clé suffixée par `-corrupt-<timestamp>`) au lieu d’être effacées.

### Mode d’emploi

1. Ouvrir `index.html` dans un navigateur moderne.
2. Créer des onglets, des catégories et des tuiles.
3. Glisser-déposer les tuiles et les catégories pour organiser le tableau de bord.
4. Cliquer régulièrement sur **Exporter** pour conserver une sauvegarde sur l’ordinateur.
5. Pour changer de machine, copier le fichier `.json` exporté et cliquer sur **Importer** sur l’autre ordinateur.

### Déploiement

Il suffit de téléverser `index.html` sur n’importe quel hébergement statique (GitHub Pages, Netlify, Vercel, Apache/Nginx, etc.). Aucune étape de compilation n’est nécessaire.

### Format du fichier de sauvegarde

Le fichier exporté est un objet JSON avec la structure suivante :

```json
{
  "app": "dashboard-tuiles",
  "version": 1,
  "exportedAt": "2026-09-07T08:41:00.000Z",
  "data": {
    "tabs": [...],
    "categories": [...],
    "tiles": [...],
    "wallpaper": "data:image/...",
    "lang": "fr",
    "hoverColor": "#4f8ff7"
  }
}
```

Les images étant intégrées sous forme de chaînes base64, le fichier de sauvegarde est autonome et peut être copié sur un autre ordinateur sans aucun fichier supplémentaire.

### Compatibilité navigateur

- Chrome / Edge / Firefox / Safari (versions récentes).
- Nécessite JavaScript et `localStorage`.

### Notes

- Les données sont attachées au profil du navigateur utilisé pour ouvrir la page. Si le même fichier est ouvert depuis une URL différente (`http` vs `https`, `www` vs domaine nu, ou chemin `file://`), le navigateur peut utiliser un espace de stockage distinct.
- Effacer les données de navigation / le `localStorage` supprimera le tableau de bord. Utilisez **Exporter** pour conserver des sauvegardes.

---

## License / Licence

Ce projet est fourni tel quel pour un usage personnel. Vous êtes libre de le modifier et de l’héberger où vous le souhaitez.

This project is provided as-is for personal use. You are free to modify and host it wherever you like.

# Broekzakdemos - branch based

Elke branch bevat de volledige MyST-boekinhoud voor één taal:
main -> engels
language-nl -> nederlands 
etc

In de root van elke branch:
- myst.yml: configuratiebestand van het boek
- export.yml en toc.yml: export- en inhoudsinstellingen
- content/: alle MyST-bestanden voor die versie

De actie: 
- Zoekt alle branches met main of die beginnen met language-.
- Bouwt elke branch afzonderlijk in een matrix (parallel).
- Wijst per branch een publicatiefolder toe:
- main → /en/, language-nl → /nl/
- Andere branches → /[branchnaam]/
- Bouwt de site met MyST CLI (myst build --html) en past de BASE_URL aan zodat alle links correct werken binnen hun subfolder.
- Uploadt alle builds als artifacts.
- Combineert alle artifacts tot één uiteindelijke site/ map.
- Voegt .nojekyll toe zodat GitHub Pages geen Jekyll-bewerking uitvoert.
- Maakt een index.html aan in de root om te redirecten naar /en/ (of alternatief gedrag via BEHAVIOR_PRIMARY).
- Deployt alles naar GitHub Pages met actions/deploy-pages@v4

Actie maakt gebruik van rootURL zoals hier: https://mystmd.org/guide/deployment-github-pages#base-url-configuration-for-github-pages 
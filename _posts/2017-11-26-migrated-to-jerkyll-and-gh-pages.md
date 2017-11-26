---
title: Blog migré sur Github pages avec Jekyll
date: 2017-11-26T17:12:00+01:00
categories:
  - Général
layout: post
---

L'informatique semble être un éternel mouvement pendulaire. Dans les années 90, les sites
web étaient statiques, puis ils ont commencé à être généré dynamiquement (avec le
`cgi-bin` et l'ère glorieuse du PHP). Aujourd'hui, on revient vers des sites statiques,
parce qu'il est assez inefficace de générer dynamiquement une page quand celle-ci ne
change pas.

## Pourquoi

Et bien, parce que mon hébergement OVH expire, et que je voulais un hébergement plus
rapide et moins cher (non pas que OVH soit cher, mais on est d'accord pour dire que ce
blog ne mérite pas d'hébergement payant).

Et justement, cela fait plusieurs années que Github offre un hébergement web à travers 
son service [Github pages][gh-pages].

Sauf que je n'ai pas envie d'écrire ma page à la main (on n'est plus en 1995 non plus).
Et c'est là que [Jekyll][jekyll] entre en jeux pour générer le site à a partir de contenu
écrit en [Markdown][md]. Ça tombe bien, j'adore la syntaxe de Markdown.
J'avoue avoir hésité un instant entre Jekyll et [hugo][hugo], mais le premier est
nativement supporté par Github.

Finalement, la seule chose qui est vraiment dynamique sur mon blog, ce sont les
commentaires, et par chance, j'utilse déjà le widget web de [Disqus][disqus].

## La migration

Sur le papier, c'est trivial: il y a un [plugin wordpress][wp-jerkyll] pour exporter
le contenu Wordpress vers des fichiers sources pour Jerkyll.

Dans la pratique:

- le plugin a quelques bugs:
  - certains exports étaient mal formatés. J'ai du les corriger manuellement.
  - le plugin a exporté de nombreux posts avec des entités HTML qui sont échapées en
    Markdown. Je n'ai pas envie de monter `&rpos;` aux visiteurs.
    Je les ai remplacées par le caractère Unicode.
  - le plugin a loupé le fait que mon blog était hébergé avec des URL prefixées de
    `/blog`.
    J'ai du mettre à jour les permalinks.
- quand j'ai changé le thème par défaut
  - j'ai eu des erreurs
    "layout post required by ….md does not exist".
    Curieux que tous les thèmes n'offrent pas tous les templates.
    Le contournement a été assez simple une fois que j'ai compris que le problème venait
    bien du thème et non de mon serveur local.
  - la page d'accueil était vide. J'ai du ajouter mon propre index.
- Pour conserver mais commentaires (avec [Disqus][disqus]), il fallait conserver
  l'identifiant. Précédemment le plugin wordpress utilisait
   `123 http://regis.decamps.info/blog/?p=123`.
  (j'avoue que je ne comprends pas pourquoi ce n'était pas simplement `123`, mais c'est
  une autre question).
  Tous les posts exportés définissaient bien une meta-donnée `id:`.
  Mais en essayant de la référencer dans le template liquide `page.id` est le permalink
  et non cette valeur `id`.
  J'ai du appliquer un autre coup de `sed` pour avoir ce `disqus_id`.

Finalement, la migration a mis quelques heures, et je suis sûr que certains posts
ne s'affichent toujours pas correctement.


[gh-pages]: https://pages.github.com/
[jekyll]: https://jekyllrb.com/
[md]: https://daringfireball.net/projects/markdown/syntax
[hugo]: https://gohugo.io/
[wp-jerkyll]: https://wordpress.org/plugins/jekyll-exporter/
[disqus]: https://disqus.com/

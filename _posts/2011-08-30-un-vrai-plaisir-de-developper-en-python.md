---
id: 2187
disqus_id: 2187 http://regis.decamps.info/blog/?p=2187
title: Un vrai plaisir de développer en Python
date: 2011-08-30T22:44:00+00:00
layout: post
guid: http://regis.decamps.info/blog/?p=2187
permalink: /blog/2011/08/un-vrai-plaisir-de-developper-en-python/
wordbooker_options:
  - 'a:9:{s:18:"wordbook_noncename";s:10:"c165552e8d";s:18:"wordbook_page_post";s:4:"-100";s:18:"wordbook_orandpage";s:1:"2";s:23:"wordbook_default_author";s:1:"1";s:23:"wordbook_extract_length";s:3:"256";s:19:"wordbook_actionlink";s:3:"300";s:18:"wordbook_attribute";s:0:"";s:29:"wordbooker_status_update_text";s:33:"New blog post :  %title% - %link%";s:17:"wordbook_new_post";s:1:"1";}'
tmac_last_id:
  - "162978333888495616"
dsq_thread_id:
  - "556982374"
categories:
  - Dev
tags:
  - Python
---
J’avais tendance à sortir des débats sur le choix du langage de programmation en me disant qu’il s’agit principalement d’un phénomène de mode, et qu’après tout, c’est l’algorithme implémenté qui compte. J’avais tort.

Car le langage est plus ou moins lisible, et cela impacte directement la qualilté de l’implémentation. Quand le code est pourri par la lourdeur de la création de variables ou de la syntaxe des structures de contrôle (boucles <tt>for</tt> et exécution conditionnelle <tt>if</tt>), c’est tout l’algorithme qui en souffre.

Il ne faut pas négliger non plus le plaisir de programmer. Un langage sympa donne envie de faire des choses.

Et en ce moment, j’ai retrouvé un vrai plaisir avec python. Par exemple, si j’ai une hashmap <tt>mot -> nombre</tt> (ça peut être un compteur d’occurence de mots) et récupérer uniquement les nombres pairs, je ne peux plus supporter la lourdeur de Java<sup>TM</sup>

    
    Map<String, Integer> dictionary = new HashMap<String, Integer>();
    dictionary.put("not", new Integer(1));
    dictionary.put("hello", new Integer(2));
    dictionary.put("world", new Integer(41));
    dictionary.put("AGAIN", new Integer(42));
    Map<String, Integer> dictionaryEven=new HashMap<String, Integer>();
    for (Map.Entry<String, Integer> entry : map.entrySet()) { 
        if (entry.getValue().intValue() % 2 == 0) {
            dictionaryEven.add(entry.getKey(), entry.getValue());
        }
    

Et je préfère nettement ce que l’on peut écrire en Python:
  
```
dictionary={« not »:1, « hello »:2, « world »:41, « again »:42}
  
dictionaryEven=dict((k,v) for k,v in dictionary.items() if v%2 == 0)
```

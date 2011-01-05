===================================
Interfaces Homme-Machine : Projet
===================================

-------------------------
 ICE Security Management
-------------------------

.. |date| date::

:Auteurs: Vincent Dupont, Robin Jarry
:date: |date|


.. |ISM| replace:: *ICE Security Management*
.. |EVE| replace:: `EVE Online`_
.. _`EVE Online` : http://www.eve-online.com
.. include:: <isopub.txt>

.. contents:: Tables des Mati�res


Description de l'Application
============================

|ISM| est une application de gestion et d'aide � la prise de d�cision pour le jeu |EVE|.

EVE Online
----------

|EVE| est un MMORPG (*Massive Multiplayer Online Role Playing Game*) d�velopp� par *CCP* qui est en production depuis 2003. Sa particularit� par rapport aux autres MMORPG est que **la partie qui a commenc� en 2003 est toujours en cours**. De plus, tous les joueurs de |EVE| jouent dans la m�me partie (et donc sur le m�me serveur). Il y a en moyenne 40.000 joueurs connect�s en *prime time* (20h-23h) europ�enne.

|EVE| est un space opera qui se d�roule dans une galaxie : *New Eden* qui comporte un peu plus de 6.000 syst�mes solaires visitables ; chacun avec son cort�ge de plan�tes et de ceintures d'ast�ro�des. Les joueurs incarnent une caste de la population de *New Eden* : les *Capsulers*. Ce sont des pilotes de vaisseaux interstellaires qui font d'une quarantaines de m�tres � plusieurs kilom�tres de long. Ces pilotes peuvent s'associer en soci�t�s appel�es *Corporations* afin de parvenir � leurs fins. 

Les possibilit�s dans |EVE| sont vari�es, chaque syst�me solaire contient des ressources naturelles qui peuvent �tre exploit�es (minerai dans les ast�ro�des, carburant dans les glaces stellaires, etc.). De l'exploitation de ces ressources, les pilotes peuvent tirer des mati�res premi�res pour construire des vaisseaux, des modules et des armes pour ceux-ci. Les vaisseaux servent principalement � faire la guerre � d'autres corporations pour conqu�rir de nouveaux syst�mes solaires mais il y a d'autres r�les comme le transport ou le minage (entre autres). Certains joueurs d�cident de jouer des espions et infiltrent des *Corporations* pour les voler ou les d�truire (cel� fait partie du jeu :-)).

Les *Corporations* sont comparables � des soci�t�s priv�es telles que nous les connaissons aujourd'hui. Elles poss�dent des comptes en banque, des bureaux, des entrep�ts et des *assets* tels que des vaisseaux, des mati�res premi�res, etc. Pour g�rer les acc�s aux entrep�ts et aux comptes, il y a un syst�me de droits assez complexe que nous ne d�crirons pas ici. Et il est n�cessaire |ndash| d�s que la corporation atteint une certaine taille (les plus grosses peuvent comporter jusqu'� 600 membres) |ndash| d'apporter une attention particuli�re � la gestion de ces droits d'acc�s, afin de limiter les risques d'infiltration et de vol. Malheureusement, l'interface du jeu est assez d�pouill�e et ne permet pas de g�rer convenablement ces droits. Notamment lorsque des joueurs arr�tent de jouer ou que des nouvelles recrues arrivent.

Les concepteurs du jeu ont mis � disposition une `API web <http://wiki.eve-id.net/APIv2_Page_Index>`_ pour obtenir des informations sur le jeu sans y �tre connect�. Cette API permet notamment de r�cup�rer le contenu de tous les hangars d'une corporation, la liste de ses membres ainsi que la liste de leurs droits.

Besoins / Sp�cifications
------------------------

Avant de d�velopper |ISM|, nous avons �tabli le cahier des charges suivants :

- Il faut un suivi pr�cis des arriv�es et des d�parts de joueurs de la corporation.
- Il faut un historique des changements de droits d'acc�s pour chaque membre.
- Chaque droit d'acc�s doit �tre pond�r� afin de pouvoir calculer le "niveau d'acc�s" potentiel d'un membre
- Il faut une vision globale du contenu des hangars de la Corporation. L'interface du jeu n'est pas satisfaisante.
- Il faut une historisation du contenu de ces hangars. Afin de pouvoir dater une disparition suspecte (� quelques heures pr�s).

Impl�mentation Technique
------------------------

Cette application se destinant � plusieurs utilisateurs en meme temps, il est sens� d'en faire une application web accessible hors jeu. 

Pour les choix de technologies, il nous fallait un langage de programmation avanc� et flexible (PHP �tait donc d�j� hors course) mais il nous fallait �galement un langage l�ger et facile � impl�menter (exit Java aussi). Il restait donc Python_ et son framework web Django_.

Les requ�tes � l'API du jeu se font par protocole http et les r�ponses sont au format XML. Nous avons utilis� la biblioth�que eveapi_ d�velopp�e en Python_ pour r�cup�rer des donn�es depuis celle-ci.

Pour la partie client, nous avons utilis� le framework javascript jQuery_ et notamment les plugins jsTree_ pour afficher le contenu des hangars et datatables_ pour g�rer les tableaux.

.. _Django : http://www.djangoproject.com/
.. _eveapi : http://wiki.eve-id.net/Eveapi
.. _Python : http://www.python.org/
.. _jQuery : http://jquery.com/
.. _jsTree : http://www.jstree.com/
.. _datatables : http://www.datatables.net/



Evolutions Possibles
--------------------

Parmi les nouvelles fonctionnalit�s utiles � impl�menter, en voici quelques unes :

- Gestion des comptes en banque de la corporation : historique des op�rations, filtre selon le type d'op�ration ou l'auteur.
- Production de diagrammes et d'indicateurs depuis les informations des comptes en banque.
- production de diagrammes sur l'�volution du niveau d'acc�s des membres.


Choix Ergonomiques
==================

Conclusion
==========

Appendice : Comment installer ISM ?
=====================================

En standalone
-------------

Derri�re un serveur Apache
--------------------------






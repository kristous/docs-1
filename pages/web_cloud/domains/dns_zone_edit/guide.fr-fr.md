---
title: 'Éditer une zone DNS OVHcloud'
excerpt: 'Découvrez comment éditer une zone DNS OVHcloud via votre espace client'
updated: 2024-05-30
---

## Objectif

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/BvrUi26ShzI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Le sigle **DNS**, signifiant **D**omain **N**ame **S**ystem, est un ensemble d'éléments (serveurs DNS, zones DNS, etc.) permettant de faire correspondre un nom de domaine avec une adresse IP.

Si besoin, consultez notre guide « [Qu'est ce qu'une zone DNS ?](pages/web_cloud/domains/dns_zone_general_information) » pour plus d'informations.

**Découvrez comment éditer votre zone DNS OVHcloud via votre espace client.**

## Prérequis

- Disposer d'un accès à la gestion du nom de domaine concerné depuis votre [espace client OVHcloud](/links/manager){.external}.
- Être connecté à votre [espace client OVHcloud](/links/manager){.external}.
- Utiliser la configuration OVHcloud (ses serveurs DNS) pour le nom de domaine concerné. 

> [!warning]
>
> - Si votre nom de domaine n'utilise pas les serveurs DNS d'OVHcloud, vous devez réaliser la modification depuis l'interface du prestataire gérant la configuration de votre nom de domaine.
> 
> - Si votre nom de domaine est enregistré chez OVHcloud, vous pouvez vérifier si ce dernier utilise notre configuration. Pour cela, rendez-vous dans votre [espace client OVHcloud](/links/manager){.external}, dans l'onglet `Serveurs DNS`{.action} du nom de domaine concerné.
> 
> Dans les deux cas ci-dessus, faites attention en effectuant vos changements de serveurs DNS. En effet, l'ancienne configuration pouvant être appliquée à votre nom de domaine ne sera plus active si vous n'avez pas préalablement reconfiguré et personnalisé la nouvelle zone DNS présente chez OVHcloud.<br>
> Vous ne pouvez avoir qu'une seule zone DNS active à la fois par nom de domaine.
>

## En pratique

### Accéder à la gestion d'une zone DNS OVHcloud

> [!primary]
>
> Contrairement au nom de domaine, il n'y a pas de notion de propriétaire pour une zone DNS, mais de gestion des contacts pour une zone DNS OVHcloud. Si vous souhaitez basculer la gestion de votre zone DNS vers un autre compte OVHcloud, suivez notre guide [Gérer les contacts de ses services](/pages/account_and_service_management/account_information/managing_contacts).

Connectez-vous à votre [espace client OVHcloud](/links/manager){.external} dans la section `Web Cloud`{.action}. Cliquez sur `Noms de domaine`{.action}, puis choisissez le nom de domaine concerné. Positionnez-vous enfin sur l'onglet `Zone DNS`{.action}.

Le tableau qui apparaît affiche pour chaque ligne un enregistrement DNS lié à votre nom de domaine chez OVHCloud. Vous avez la possibilité d'en filtrer le contenu par type d'enregistrement ou par domaine.

![dnszone](images/tab.png){.thumbnail}

### Éditer la zone DNS OVHcloud de votre nom de domaine

Vous pouvez éditer la zone DNS OVHcloud de votre nom de domaine en ajoutant, modifiant ou en supprimant un enregistrement DNS. Pour cela, deux possibilités s'offrent à vous :

#### Modifier manuellement la zone en mode textuel <a name="txtmod"></a>

> [!warning]
>
> Pour les utilisateurs avertis uniquement. Soyez également très vigilant sur la syntaxe lors de vos modifications.
>

Depuis l'onglet `Zone DNS`{.action}, cliquez sur `Modifier en mode textuel`{.action} puis suivez les étapes qui s'affichent.

> [!warning]
> 
> Ne modifiez pas, via le bouton `Modifier en mode textuel`{.action}, les enregistrements NS de votre zone DNS au profit de serveurs DNS externes à OVHcloud. En effet, cette zone DNS fonctionne **uniquement** avec des serveurs DNS OVHcloud.

#### Utiliser nos assistants de configuration

À partir de ce point, cette documentation abordera uniquement la configuration via nos assistants.

> [!primary]
>
> Munissez-vous des informations à modifier dans votre zone DNS OVHcloud. Si vous effectuez cette modification à la demande d'un fournisseur de service, ce dernier doit vous communiquer la liste des éléments à modifier.
>

#### Ajouter un nouvel enregistrement DNS

Pour ajouter un nouvel enregistrement DNS, depuis l'onglet `Zone DNS`{.action} de votre nom de domaine, cliquez sur le bouton `Ajouter une entrée`{.action} à droite du tableau. Sélectionnez le type de champ DNS puis suivez les étapes.

Nous vous invitons à vérifier au préalable si cet enregistrement n'existe pas déjà et ne pointe pas vers une cible différente. Pour cela, filtrez le contenu du tableau par type d'enregistrement ou par domaine. Si l'enregistrement existe déjà, nous vous invitons à le modifier grâce à la manipulation décrite juste après.

![dnszone](images/add-an-entry.png){.thumbnail}

> Lorsque la cible de votre enregistrement est une URL, pensez à ponctuer celle-ci. En effet, si vous ne le faites pas, votre nom de domaine sera automatiquement ajouté à la fin de votre cible.
>
> Exemple : vous souhaitez créer un enregistrement CNAME de *test.mydomain.ovh* vers *mydomain.ovh*.
>
> Vous devez alors avoir comme cible *mydomain.ovh.* et non pas *mydomain.ovh* sans le **.** à la fin.

#### Modifier un enregistrement DNS existant

Pour modifier un enregistrement DNS, toujours depuis l'onglet `Zone DNS`{.action} de votre espace client, cliquez sur le pictogramme `...`{.action} dans le tableau à droite de l'entrée choisie. Cliquez ensuite sur `Modifier l'entrée`{.action} puis suivez les étapes qui s'affichent.

![dnszone](images/modify-record.png){.thumbnail}

#### Supprimer un enregistrement DNS

Pour supprimer un enregistrement DNS, toujours depuis l'onglet `Zone DNS`{.action} de votre espace client, cliquez sur le pictogramme `...`{.action} dans le tableau à droite de l'entrée choisie. Cliquez ensuite sur `Supprimer l'entrée`{.action} puis suivez les étapes qui s'affichent.

Vous pouvez supprimer plusieurs entrées en une seule fois en les cochant depuis la partie gauche du tableau, puis en cliquant sur le bouton `Supprimer`{.action}.

![dnszone](images/delete-record.png){.thumbnail}

#### Réinitialiser la zone DNS

Réinitialiser votre zone DNS permet de revenir à une configuration minimale, avec les entrées OVHcloud par défaut ou celles de vos services. Vous pouvez également pointer votre nom de domaine vers des services d'hébergement Web et e-mail personnalisés .

> [!alert]
>
> Avant de réinitialiser votre zone DNS, assurez-vous que votre nom de domaine n'est pas attaché à des services en cours d'utilisation, tels qu'un site web ou des adresses e-mail.
>

Depuis l'onglet `Zone DNS`{.action}, cliquez sur `Réinitialiser ma zone DNS`{.action} puis suivez les 2 étapes qui s'affichent.

![dnszone](images/reset-my-dns-zone.png){.thumbnail}

**Étape 1**

Répondez à la question `Voulez-vous activer les entrées minimales lors de la réinitialisation de votre zone DNS ?`. Définir des entrées minimales dans une zone DNS permet d'éviter qu'une requête vers le nom de domaine n'aboutisse pas sur une erreur.

- `Oui, je veux réinitialiser ma zone DNS avec les entrées minimales`
- `Non, mais je veux réinitialiser ma zone DNS`

**Étape 2**

Quel que soit votre choix à l'étape 1, il est nécessaire de définir une réponse lorsqu'on interroge votre nom de domaine pour éviter une réponse DNS en erreur.

Sélectionnez les deux options en cliquant sur les onglets suivants.

> [!tabs]
> **Adresse IP de votre hébergement**
>> - `Redirection`: votre nom de domaine pointera vers le serveur de redirection OVHcloud. Cela permet d'afficher une page d'accueil OVHcloud et ainsi éviter une erreur DNS.<br>
>> - `Hébergement Web OVHcloud`: Votre nom de domaine pointera vers l'adresse IP de l'hébergement Web associé au nom de domaine. <br>
>> - `Personnalisé`: définissez la valeur IPv4 ([enregistrement A](#pointer-records)) de l'hébergement Web que vous souhaitez pointer. <br><br>
>> ![dnszone](images/dns-zone-reset-01.png){.thumbnail}
>>
> **Adresse de votre serveur mail**
>> - `Redirection`: votre nom de domaine pointera vers les serveurs de redirections e-mail. Ce choix. Il est particulièrement utile si vous n'avez aucune offre e-mail mais que vous souhaitez renvoyer les e-mails vers une ou plusieurs adresses e-mails en dehors de votre nom de domaine.<br>
>> - `Serveur E-mail OVHcloud`: à définir lorsque que vous possédez une offre e-mail mutualisée.<br>
>> - `Personnalisé`: définissez l'URL et la priorité du serveur e-mail ([enregistrement MX](#mail-records)) que vous souhaitez pointer.<br><br>
>> ![dnszone](images/dns-zone-reset-01.png){.thumbnail}
>>

### Le temps de propagation

Une fois la zone DNS de votre nom de domaine modifiée, un temps de propagation de 24 heures maximum est nécessaire afin que les modifications soient effectives.

Si vous souhaitez réduire ce délai pour les prochaines éditions de votre zone DNS OVHcloud, vous pouvez le modifier, dans une certaine mesure, en ajustant le TTL (*Time To Live*) qui s'appliquera à tous les enregistrements de la zone DNS.
Pour ce faire, positionnez-vous sur l'onglet `Zone DNS`{.action} de votre espace client, cliquez sur le bouton `TTL par défaut`{.action} puis suivez les étapes qui s'affichent.

Vous pouvez aussi modifier le TTL d'un enregistrement DNS. Cependant, cette manipulation ne peut être effectuée que sur un enregistrement à la fois, en le modifiant ou lors d'un ajout.

### Cas particulier d'usage : l'utilisation des enregistrements CNAME <a name="techusecase"></a>

Certains utilisateurs créent des zones DNS directement pour le sous-domaine d’un domaine (par exemple *subdomain-with-its-own-DNS-zone.mydomain.ovh*). La règle précisée [plus haut](#cname) dans ce guide s’applique alors également dans ce cas de figure.

La zone DNS étant créée pour le sous-domaine (dans notre exemple *subdomain-with-its-own-DNS-zone.mydomain.ovh*), ce dernier est alors considéré comme un domaine à part entière dans sa zone DNS.

De ce fait et dans ce cas bien spécifique, vous ne pourrez pas créer un champ CNAME pour *subdomain-with-its-own-DNS-zone.mydomain.ovh* dans la zone DNS que vous avez créé pour celui-ci. Vous pourrez cependant créer des champs CNAME tels que *subdomain.subdomain-with-its-own-DNS-zone.mydomain.ovh* ou *xxx.subdomain-with-its-own-DNS-zone.mydomain.ovh*.

## Aller plus loin

[Généralités sur les serveurs DNS](/pages/web_cloud/domains/dns_server_general_information){.external}.

[Ajouter un champ SPF à la configuration de son nom de domaine](/pages/web_cloud/domains/dns_zone_spf){.external}.

[Protégez votre domaine contre le Cache Poisoning avec le DNSSEC](/links/web/domains-dnssec){.external}.

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>.
---
title: "Qu'est ce qu'une zone DNS ?"
excerpt: 'Découvrez le rôle d'une zone DNS, ce qu'elle contient et comment elle fonctionne avec un nom de domaine'
updated: 2024-05-30
---

## Objectif

Le sigle **DNS**, signifiant **D**omain **N**ame **S**ystem, est un ensemble d'éléments (serveurs DNS, zones DNS, etc.) permettant de faire correspondre un nom de domaine avec une adresse IP.

Il est essentiel de différencier les **serveurs DNS** et la **zone DNS**. En effet, c'est au niveau du **serveur DNS** qu'est configurée la **zone DNS**. 

Vous trouvez les informations relatives aux **serveurs DNS** sur notre guide « [Qu'est ce qu'un serveur DNS](/pages/web_cloud/domains/dns_server_general_information) ».

Par exemple, lorsque vous souhaitez accéder au site *mydomain.ovh* via un navigateur internet, votre requête est initialement traitée par cet ensemble DNS qui va l'aiguiller vers l'adresse IP du serveur hébergeant le site *mydomain.ovh*.

Ainsi, lorsque vous tapez *mydomain.ovh*, les **serveurs DNS** associés à ce nom de domaine seront interrogés. Ces derniers contiennent la **zone DNS** du nom de domaine *mydomain.ovh* où est renseignée l'adresse IP de l'hébergement de *mydomain.ovh*. Votre navigateur est ensuite en mesure d'afficher le site internet *mydomain.ovh* contenu sur l'hébergement web. On appelle cela une résolution DNS.

![DNS](images/dns-resolution.gif){.thumbnail}

**Découvrez le rôle d'une zone DNS, ce qu'elle contient et comment elle fonctionne avec un nom de domaine.**

## En pratique

### Rôle d'une zone DNS

La zone **D**omain **N**ame **S**ystem (**DNS**) d’un nom de domaine constitue le fichier de configuration de ce dernier. Elle se compose d’informations techniques, appelées *enregistrements DNS*. La zone DNS est, en quelque sorte, comme un centre d'aiguillage pour un nom de domaine.

![DNS](images/dns-zone-mydomain-ovh.png){.thumbnail}

Vous pouvez, par exemple, y préciser :

- L'adresse IP (enregistrements DNS de type *A* et *AAAA*) de votre hébergement web pour afficher votre site web avec votre nom de domaine.
- Les serveurs e-mail (enregistrements DNS de type *MX*) vers lesquels votre nom de domaine doit rediriger les e-mails qu'il reçoit. Cela vous permet de les consulter sur votre (vos) adresse(s) e-mail(s) personnalisée(s) avec votre nom de domaine.
- Des informations liées à la sécurité / l'authentification de vos services (hébergement web, serveur web, serveur e-mail, etc.)  associés à votre nom de domaine (enregistrements DNS de type *SPF*, *DKIM*, *DMARC*, etc.).

Une zone DNS est hébergée / enregistrée sur des **serveurs DNS**. Ce sont les **serveurs DNS** qui doivent être déclarés auprès du nom de domaine pour utiliser la zone DNS qu'ils hébergent. 

### Les enregistrements DNS

**L'édition d'une zone DNS est une manipulation sensible** : réaliser un changement inopportun pourrait, par exemple, rendre impossible l'accès à votre site internet ou la réception de nouveaux messages sur vos adresses e-mail.

Comprendre ces différents enregistrements vous permettra de mieux appréhender les changements que vous allez effectuer si vous [éditez la zone DNS](/pages/web_cloud/domains/dns_zone_edit) de votre nom de domaine. Nous vous invitons vivement à consulter la liste ci-dessous. Elle reprend les objectifs et spécificités de chaque enregistrement.

#### Enregistrements de pointage <a name="pointer-records"></a>

Sélectionnez l'enregistrement de votre choix en cliquant sur chacun des onglets suivants.

> [!tabs]
> **A**
>> **A**ddress <br><br>
>> Relie un nom de domaine à une adresse IPv4 `X.X.X.X` (où les `X` sont des chiffres compris entre `0` et `255`). Par exemple, l'adresse IPv4 du serveur où est hébergé votre site web.
>>
> **AAAA**
>> 4 lettres **A** car cet enregistrement est encodé sur quatre fois plus de bits que le champ de pointage **A** historique <br><br>
>> Relie un nom de domaine à une adresse IPv6. Par exemple, l'adresse IPv6 du serveur où est hébergé votre site web.
>>
>> > [!primary]
>> > Les adresses IPv6 sont progressivement mises en place pour pallier au manque d'adresses IPv4 dû à l'expansion continue des usages numériques. L'encodage sur 128 bits des adresses IPv6 permet ainsi de fournir un plus grand nombre d'adresses IP.
>> >
>> > Néanmoins, si votre serveur dispose déjà d'une IPv4, nous vous recommandons de privilégier l'utilisation de celle-ci à votre IPv6.<br>
>> > En effet, les IPv6 ne sont pas encore correctement interprétées sur l'ensemble du réseau Internet, ce qui peut engendrer des perturbations d'affichage ou d'accès.
>
> **CNAME**
>> **C**anonical **NAME** <br><br>
>> Utilise l'adresse IP d'un autre nom de domaine en créant un lien appelé alias. Par exemple, si *www.mydomain.ovh* est un alias de *mydomain.ovh*, cela indique que *www.mydomain.ovh* utilisera l'adresse IP de *mydomain.ovh*.
>>
>> > [!alert]
>> >
>> > Un enregistrement TXT utilisant le même domaine ou sous-domaine qu'un enregistrement CNAME perturbe le fonctionnement de ce dernier. Votre enregistrement CNAME ne fonctionnera alors que partiellement ou pas du tout.
>> 
>> > [!warning]
>> >
>> > Par convention, les champs CNAME ne peuvent pas être directement utilisés par un domaine dans sa propre zone DNS. En effet, le domaine seul doit obligatoirement et directement pointer vers une adresse IP avec un champ de type A (ou AAAA s’il s’agit d’une IPv6).
>> > 
>> > Pour reprendre l’exemple donné ci-dessus, vous ne pourrez pas créer un champ CNAME pour le domaine *mydomain.ovh* dans la zone DNS que vous avez créé pour celui-ci.
>> > Vous pourrez cependant créer des champs CNAME avec tous les sous-domaines (exemples : *subdomain.mydomain.ovh* ou *www.mydomain.ovh*) du domaine *mydomain.ovh* dans la zone DNS créée pour *mydomain.ovh*.
>> >
>> > Si vous souhaitez aller plus loin techniquement sur ce sujet, vous pouvez retrouver, en bas de cette page, [un cas particulier d’usage concernant les CNAME et les zones DNS créées pour des sous-domaines](#techusecase).
>>
> **Champ DNAME**
>> **D**elegation **NAME** <br><br>
>> Permet de générer un « alias » pour l’ensemble des sous-domaines d’un domaine. Cet enregistrement évite de créer une multitude d’enregistrements CNAME. En effet, un champ CNAME ne redirige indépendamment qu'un seul sous-domaine vers une seule cible. Exemple : en créant un enregistrement DNAME de *mydomain.ovh* vers *ovh.com*, tous les sous-domaines de *mydomain.ovh* (tels que *dname.mydomain.ovh* et *xxx.mydomain.ovh*) seront redirigés respectivement vers les sous-domaines de *ovh.com* (tels que *dname.ovh.com* et *xxx.ovh.com*). En d’autres termes, l’enregistrement DNAME indique que *dname.mydomain.ovh* et *xxx.mydomain.ovh* doivent respectivement afficher les résultats de *dname.ovh.com* et *xxx.ovh.com*.
>>
>> > [!warning]
>> >
>> > En revanche, *mydomain.ovh* en tant que domaine n’affichera pas la cible du domaine *ovh.com* car l’enregistrement DNAME n’est valable que pour les sous-domaines des domaines définis dans l’enregistrement DNAME.
>> >
>> > De plus, en reprenant l'un des exemples ci-dessus, si le sous-domaine cible *xxx.ovh.com* ne pointe nulle part, alors l’enregistrement DNAME n’affichera rien non plus pour *xxx.mydomain.ovh*.
>> 
>> > [!success]
>> >
>> > L’enregistrement DNAME est généralement utilisé dans le cadre d’un changement de nom de société. Il peut aussi être mis en place lorsqu’un utilisateur dispose de plusieurs extensions de domaines (.fr, .net, .com, .info, …) pour les rediriger entre eux facilement.
>> >
> **Champ NS**
>> **N**ame **S**erver <br><br>
>> Définit les serveurs DNS associés à votre zone DNS. Par exemple, si les enregistrements NS de votre zone DNS affichent les serveurs *dnsXX.ovh.net* et *nsXX.ovh.net*, vous devrez alors utiliser ces derniers dans l'onglet `Serveurs DNS`{.action} de votre espace client OVHcloud. Consultez notre documentation « [Modifier les serveurs DNS d’un nom de domaine OVHcloud](/pages/web_cloud/domains/dns_server_edit) » pour plus d'informations.
>>
>> > [!warning]
>> > 
>> > Ne modifiez pas, via le bouton `Modifier en mode textuel`{.action}, les enregistrements NS de votre zone DNS au profit de serveurs DNS externes à OVHcloud. En effet, cette zone DNS fonctionne **uniquement** avec des serveurs DNS OVHcloud.
>> 

#### Enregistrements e-mail <a name="mail-records"></a>

Sélectionnez l'enregistrement de votre choix en cliquant sur chacun des onglets suivants.

> [!tabs]
> **MX**
>> **M**ail e**X**changer <br><br>
>> Relie un nom de domaine à un serveur e-mail. Par exemple, l'adresse *10 mx1.mail.ovh.net* correspond à l'un des serveurs e-mail OVHcloud lorsque vous possédez une offre e-mail OVHcloud. Il est probable que votre fournisseur e-mail dispose de plusieurs serveurs e-mail : plusieurs champs MX doivent donc être créés. Consultez notre documentation « [Ajouter un champ MX à la configuration de son nom de domaine](/pages/web_cloud/domains/dns_zone_mx) ».
>>
>> > [!warning]
>> >
>> > De manière générale, il est recommandé de n’utiliser qu’un ou plusieurs serveurs d’un même fournisseur e-mail dans votre zone DNS.
>> > En effet, si vous disposez déjà de services e-mail chez un autre fournisseur e-mail et que vous ajoutez en parallèle (sans remplacer) les serveurs e-mail de votre nouveau fournisseur e-mail, vous risquez de recevoir aléatoirement vos e-mails chez l’un ou l’autre de vos deux fournisseurs.
> **SPF**
>> **S**ender **P**olicy **F**ramework <br><br>
>> Permet d'éviter les potentielles usurpations d’identité sur les adresses e-mail utilisant votre nom de domaine (*spoofing*). Par exemple, l'enregistrement `v=spf1 include:mx.ovh.com ~all` indique que seuls les serveurs d'envoi liés à votre offre mail OVHCloud peuvent être considérés comme légitimes par le serveur de réception. Vous pouvez renseigner cet enregistrement sous la forme d'un champ TXT ou via notre système de configuration automatique. Consultez notre documentation « [Ajouter un champ SPF à la configuration de son nom de domaine](/pages/web_cloud/domains/dns_zone_spf) » pour en savoir plus.
>>
> **DKIM**
>> **D**omain**K**eys **I**dentified **M**ail <br><br>
>> Permet de vérifier l'authenticité du nom de domaine de l'expéditeur et assurer l'intégrité de l'e-mail envoyé. L'enregistrement DKIM se présente sous la forme d'une clé composée de plusieurs caractères. La clé DKIM est fournie par votre prestataire e-mail (si cette fonctionnalité est proposée par ce dernier), il est possible de la renseigner sous la forme d'un champ TXT.
>>
> **DMARC**
>> **D**omain-based **M**essage **A**uthentication, **R**eporting and **C**onformance <br><br>
>>Contribue à l'authentification des e-mails en association avec les méthodes SPF et/ou DKIM. Cette valeur vous sera donnée par votre fournisseur e-mail (si cette fonctionnalité est proposée par ce dernier), elle sera au minimum associée à un enregistrement SPF ou DKIM.

#### Enregistrements étendus <a name="extented-records"></a>

Sélectionnez l'enregistrement de votre choix en cliquant sur chacun des onglets suivants.

> [!tabs]
> **TXT**
>> **T**e**XT** <br><br>
>> Permet d'ajouter la valeur de votre choix, au format textuel, dans la zone DNS de votre nom de domaine. Cet enregistrement est souvent utilisé lors de processus de vérification/validation ou de sécurité.
>>
>> > [!warning]
>> >
>> > L'enregistrement TXT est limité à 255 caractères. Il est néanmoins possible, dans certains cas, de scinder votre valeur en plusieurs enregistrements. Renseignez-vous auprès de votre prestataire lorsque celui-ci vous demande de renseigner une valeur dépassant le quota des 255 caractères.
>> >
>> > Cette limite n'est cependant pas existante si vous passez par la fonctionnalité « Modifier en mode textuel » [décrite plus bas](#txtmod) dans ce guide (pour les utilisateurs avertis).
>>
> **SRV**
>> **S**e**RV**ice resource <br><br>
>> Permet d'indiquer l'adresse d'un serveur gérant un service. Par exemple, il peut indiquer l'adresse d'un serveur SIP ou celle d'un serveur permettant la configuration automatique d'un logiciel de messagerie.
>>
> **CAA**
>> **C**ertification **A**uthority **A**uthorization <br><br>
>> Permet de lister les autorités de certification autorisées à délivrer des certificats SSL pour un nom de domaine.
>>
>> > [!warning]
>> >
>> > Si vous configurez une entrée CAA pour un nom de domaine, cette configuration s'appliquera également à **tous les sous-domaines** de ce même nom de domaine.
>> >
>> > Si vous utilisez un certificat SSL Let's Encrypt avec votre domaine sur un hébergement mutualisé OVHcloud et que vous utilisez un enregistrement CAA, ce dernier empêchera la régénération du certificat SSL Let's Encrypt.
>>
> **NAPTR**
>> **N**ame **A**uthority **P**oin**T**e**R** <br><br>
>> Utilisé en télécommunication pour diriger une requête émise par un terminal mobile vers un serveur. Un enregistrement SRV peut y être associé pour générer de façon dynamique des URIs (Uniform Resource Identifier) cibles.
>>
> **LOC**
>> **LOC**ation <br><br>
>> Utilisé pour renseigner les informations de position géographique (notamment avec la latitude, la longitude et l'altitude).
>>
> **SSHFP**
>> **S**ecure **SH**ell **F**inger**P**rint <br><br>
>> Utilisé pour renseigner l'empreinte d'une clé publique SSH.
>>
> **TLSA**
>> **T**ransport **L**ayer **S**ecurity **A**uthentification <br><br>
>> Utilisé pour renseigner l'empreinte d'un certificat SSL/TLS.
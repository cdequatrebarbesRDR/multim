# MULTIMARQUE

## Requirements 
- [ ] Droits d'accès à la BDD via le VPN
- [ ] Accès au réseau S://


## Contexte
Contrat Assuré (PREV, MAL)
appartient à 1 Plusieurs marques:
* ROEDERER
* SIMAX
* CALIOPE
* EOLE


Assuré A 
- PREV => Roederer 
- MAL => SIMAX


Site web: problème d'accès

AS400 renvoie la 1ere ligne trouvée pour l'assuré 
EXTRACTION à plat étant donné

APPEL à l'API de l'INFOCENTRE


Table Assuré "dtwpers"

adhe_cntr_id


Personne > Assuré Contrat > Contrat Entreprise


Numéro de personne (LOGIN ) Attention pas unique RANG Bénéficiaire RANG INT == 0 Assuré principal Salarié du client

range (2,9) Conjoint
range (11, 20) Enfants
range (21, 30) Enfants cas spécifiques (handicapés adultes)
range (51, 99) Ascendants (parents, )

RANG 2 Conjoint
RANG 3 

PERS_ID NUMERO_ASSURE* 100 + RANG (99) (AS400 COMPAT)
a chercher dtw_adhe (CONTRAT ADHERENT) tous les contrats des assurés 
filtré par date de validité :
- date_debut < Today date_fin >= Today or Null
- statut ACT ANI (Annulé et invisible: VIDE) ANV (Annulé et visible: PAS VIDE) quand annulé DATE DEBUT ET DATE DE FIN ==
-> ADHE_CNTRIDS (AS400 NUMPER)
- ADHE_ID (AS 400 NUMPER)
  filtré par date de validité :
- date_debut < Today date_fin >= Today or Null
- statut ACT ANI (Annulé et invisible: VIDE) ANV (Annulé et visible: PAS VIDE) quand annulé DATE DEBUT ET DATE DE FIN ==

-> AGEN (MUTUELLE/AGENCE)
CNRT_AGEN_ID
AGEN_PORTEFEUILLE 001 RDR 051 SIMAX 060 EOLE 
CALLIOPE (ID AGE)


-> TYpe de produit (PRDT)
CNTR_ID
CNTR_PRD_ID
PRDT_PRODUIT
PRDT_OPTION
PRDT_LIBELLE
PRDT_FAMILLE (PRE, MAL, OBS, DIV)



GCAB GROUPE-ENTREPRISE-CATEGORIE-ASSURE_NB-B_RANG



## Compléments

Que veut comme données le pole WEB a partir d'un N° Assuré? 
> Le plus d'info possibles`

- Assuré et Entreprise
- N° entreprise N° Adhérent
- Coordonnées
- Les numéros de contrats
- Les services web IBA

ENDPOINT Assurés Entreprise

- /assures/<NUMERO_ASSURE>/contrats
- /assures/<NUMERO_ASSURE>/services
- /entreprise/<NUMERO_ENTREPRISE>/contrats
- /entreprise/<NUMERO_ENTREPRISE>/services

? BENEFICAIRES => AS400
- /assures/<NUMERO_ENTREPRISE>/beneficiaires?
- /entreprises/<NUMERO_ENTREPRISE>/beneficiaires?

- CARTE "ValidationCode" <= AS400 check if valid with hash


- Fichier d'exemple envoyé  
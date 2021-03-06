---
id: 253c8cb9-357c-4fd2-a868-eed7233f3ea2
title: Sparql
desc: ''
updated: 1624633934500
created: 1611593110381
---

# SPARQL queries


## All organisms containing compound for which a given MeSh id has been reported.

Change MeSH Id according to https://meshb.nlm.nih.gov/search

https://w.wiki/vo9

### displayed as a treemap

https://w.wiki/zkK


## compounds in organisms who have a parent taxon with a given taxon name

https://w.wiki/vo$

## compounds in organisms who have a parent taxon with a given taxon name - grouped and counted 

https://w.wiki/368M

## compounds in organisms who have a parent taxon with a given taxon name - with mf and accurate mass


https://w.wiki/36Ki



## compounds displaying a found in a taxon property

https://w.wiki/q$H

## idsm powered !!!


https://w.wiki/xMJ

[[mail_jakub|scratch.2021.02.02.150258.mail_jakub]] 

## genus counting indole substrutcures

This SPAQRL query is based on a proposition of Jakub Galgonek <jakub.galgonek@uochb.cas.cz> (https://idsm.elixir-czech.cz/) and adapted by Pierre-Marie Allard (pierre-marie.allard@unige.ch)
It returns an order list of organisms known to produce chemical compounds having an indolic moiety.
The organisms are aggregated at the parent taxon level, and the list is ordered by number of compound occurence in the parent t

https://w.wiki/xMN


## all molecules isolated by author X

https://w.wiki/32D6
https://w.wiki/32$m


## count of the authors having isolated a given scaffold

https://w.wiki/32DF

## compare authors by count of compound

https://w.wiki/32Vb
https://w.wiki/32Vk (bar-chart)


## compare authors by count of compound (substructure-refinable)

https://w.wiki/32Vd

## compare authors by count of compound (structuresimilarity-refinable)

https://w.wiki/32Vg (indolic)

https://w.wiki/32Vj (bubblechart - indolic)
https://w.wiki/32Vi (bubblechart - tropanic)

## count of authors isolating substances with a given role

https://w.wiki/32Vr

## all distinct article/substances/org for a given biological role

https://w.wiki/32Vu

## all disticnt antibiotics

https://w.wiki/32Vv


## drug-prot interaction 

```SPARQL
SELECT DISTINCT ?parent_taxon ?parent_taxon_name ?compound ?interaction ?compoundLabel ?geneLabel ?biological_processLabel ?diseaseLabel WHERE {
  #?compound wdt:P2868 ?mesh.
  #?mesh wdt:P486 "D000962".
  ?compound wdt:P235 ?inchikey.
  {
    ?compound p:P703 ?statement.
    ?statement ps:P703 ?taxon.
    ?taxon wdt:P171 ?parent_taxon.
    OPTIONAL { ?taxon wdt:P171 ?parent_taxon. }
    OPTIONAL { ?parent_taxon wdt:P225 ?parent_taxon_name. }
    {
      ?statement prov:wasDerivedFrom ?ref.
      ?ref pr:P248 ?reference.
      ?reference wdt:P356 ?reference_doi;
        wdt:P1476 ?reference_title.
    }
   #?compound p:P129 ?interaction.
   #?interaction wdt: wd:Q21119831.
    
    ?compound wdt:P129 ?gene_product .   # drug interacts with a gene_product
    ?gene wdt:P688 ?gene_product .  # gene_product (usually a protein) is a product of a gene (a region of DNA)
    ?disease  wdt:P2293 ?gene .    # genetic association between disease and gene
    ?disease wdt:P279*  wd:Q12078 .  # limit to cancers wd:Q12078 (the * operator runs up a transitive relation..)
    ?gene_product wdt:P682 ?biological_process . #add information about the GO biological processes that the gene is related to 

    ?biological_process (wdt:P361|wdt:P279)* wd:Q14599311.
  }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
  
GROUP BY ?parent_taxon ?parent_taxon_name ?compound ?interaction ?compoundLabel ?geneLabel ?biological_processLabel ?diseaseLabel
#ORDER BY DESC (?count)
```


## Generic LOTUS queries

https://w.wiki/$Q$
https://w.wiki/$R3
https://w.wiki/$RD apparently working !
https://w.wiki/$RR with wd: for structure and org
https://w.wiki/$RU wd: for everyone ...still ok
https://w.wiki/$SF full monty

## Sachem non-permanent endpoint

https://idsm.elixir-czech.cz:2443/sachem/#/search


## Sachem grand parents https://w.wiki/32Wz

## Retrun compound present in invasive species

https://w.wiki/32fa
https://w.wiki/32fc

## check taxon for a givin INChikey (regex)

https://w.wiki/32j3

## chemotax graph queries

https://w.wiki/32q9
https://w.wiki/32qC


https://w.wiki/32qN


# to tweet 

All the compounds found in the Streptomyces avermitilis taxon and the references documenting this link. 
https://w.wiki/33V$

We can remove the references to get all unique compounds found in the Streptomyces coelicolor

https://w.wiki/33WG



All the biological taxa where the chemical compound erysodine is found in.
https://w.wiki/33WA


# all compounds produced by a given taxon or group of taxa (including children taxa) which have a described bioactivity : 

https://w.wiki/3YMo

resumed as treemap https://w.wiki/3YMt


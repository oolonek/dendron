---
id: 235ba226-b0da-4c23-bbb7-c46c4a65d2f1
title: Create_item
desc: ''
updated: 1614448753481
created: 1614258921986
---

# Manual addition of a documented structure-organism pair to Wikidata


## Fetching the information for the documented structure-organism pair

### Structure

Search pubchem for your compound, here Trigocherrin A
https://pubchem.ncbi.nlm.nih.gov/compound/101556657

![](/assets/images/2021-02-25-14-15-54.png)

Fetch its name, InChIKey, InChI, Canonical and Isomeric SMILES.
Here we keep, respectively:

```
* trigocherrin A
* QOVGHDRCAGYGEB-FFZYJECLSA-N
* InChI=1S/C38H36Cl2O12/c1-18(2)35(44)27-19(3)37-25-16-24(31(39)40)28(48-32(43)22-12-8-6-9-13-22)36(25,45)33(47-21(5)42)34(17-46-20(4)41)29(49-34)26(37)30(35)51-38(50-27,52-37)23-14-10-7-11-15-23/h6-16,19,26-30,33,44-45H,1,17H2,2-5H3/t19-,26+,27?,28+,29+,30-,33-,34+,35+,36-,37+,38?/m1/s1
* CC1C2C(C3C4C1(C5=CC(=C(Cl)Cl)C(C5(C(C6(C4O6)COC(=O)C)OC(=O)C)O)OC(=O)C7=CC=CC=C7)OC(O2)(O3)C8=CC=CC=C8)(C(=C)C)O
* C[C@@H]1C2[C@]([C@H]3[C@H]4[C@]1(C5=CC(=C(Cl)Cl)[C@@H]([C@]5([C@@H]([C@@]6([C@H]4O6)COC(=O)C)OC(=O)C)O)OC(=O)C7=CC=CC=C7)OC(O3)(O2)C8=CC=CC=C8)(C(=C)C)O
```
### Organism

You can check if your organism name is correctly spelled using the Global Names resolver service 

http://gni.globalnames.org/name_strings?search_term=trigonostemon+cherrieri&commit=Search

![](/assets/images/2021-02-27-18-40-20.png)

Alternatively you can use gnfinder in your command line interface to check for the spelling of your organism string.
 
Beloow you see that the misspelled _Trigonstemion cherrieri_ is correctly resolved to _Trigonostemon cherrieri_.

```echo "Trigonostemion cherrieri" | gnfinder find -c -l eng

{
  "metadata": {
    "date": "2021-02-27T18:44:41.640982+01:00",
    "gnfinderVersion": "v0.11.1",
    "withBayes": true,
    "tokensAround": 0,
    "language": "eng",
    "detectLanguage": false,
    "totalWords": 2,
    "totalCandidates": 1,
    "totalNames": 1
  },
  "names": [
    {
      "cardinality": 2,
      "verbatim": "Trigonostemion cherrieri",
      "name": "Trigonostemion cherrieri",
      "odds": 77581.46698350731,
      "start": 0,
      "end": 24,
      "annotationNomenType": "NO_ANNOT",
      "annotation": "",
      "verification": {
        "bestResult": {
          "dataSourceId": 1,
          "dataSourceTitle": "Catalogue of Life",
          "taxonId": "1575885",
          "matchedName": "Trigonostemon cherrieri Veillon",
          "matchedCardinality": 2,
          "matchedCanonicalSimple": "Trigonostemon cherrieri",
          "matchedCanonicalFull": "Trigonostemon cherrieri",
          "classificationPath": "Plantae|Tracheophyta|Magnoliopsida|Malpighiales|Euphorbiaceae|Trigonostemon|Trigonostemon cherrieri",
          "classificationRank": "kingdom|phylum|class|order|family|genus|species",
          "classificationIds": "3939764|3942634|3942724|3942777|3942795|4210752|1575885",
          "editDistance": 1,
          "stemEditDistance": 1,
          "matchType": "FuzzyCanonicalMatch"
        },
        "dataSourcesNum": 13,
        "dataSourceQuality": "HasCuratedSources",
        "retries": 1
      }
    }
  ]
}
```

### Reference

Make sure that you have the correct reference DOI.
Here : **10.1021/ol2030907**

## Checking for the presence of your compound in Wikidata

Using the InChIKey, run a SPARQL query to check if your compound is not present in wikidata.
Adapt the query by pasting your own InChIkey

https://w.wiki/32WF

If your compound is already present you can directly skip to the Add the found in taxon statement section below.

## Adding your data manually to Wikidata.

First you will need to create a Wikidata account [https://www.wikidata.org/w/index.php?title=Special:CreateAccount&returnto=Wikidata%3AMain+Page](https://www.wikidata.org/w/index.php?title=Special:CreateAccount&returnto=Wikidata%3AMain+Page)

Then you can start by reading the Wikidata introduction page [https://www.wikidata.org/wiki/Wikidata:Introduction](https://www.wikidata.org/wiki/Wikidata:Introduction) and have a look at the Wikidata Tours page [https://www.wikidata.org/wiki/Wikidata:Tours](https://www.wikidata.org/wiki/Wikidata:Tours)

Now that we are all set up, you can go on the wikidata create new item page [https://www.wikidata.org/wiki/Special:NewItem](https://www.wikidata.org/wiki/Special:NewItem)


![](/assets/images/2021-02-25-14-18-03.png)

An empty page with a new wikidata identifier is created 

![](/assets/images/2021-02-25-14-18-50.png)

### Adding the chemical compound information 

Create a new statement 'is an instance of'

![](/assets/images/2021-02-25-14-20-08.png)

and select chemical compound 

![](/assets/images/2021-02-25-14-20-58.png)

Since your created a new object which is an instance of a chemical compound, the new statements related to chemical compounds will be automatically proposed.

![](/assets/images/2021-02-25-14-22-44.png)

You can go on and fill them

Here we start by the InChIKey. 
Mind the little flag which will automatically tell you if you have some problems with the recently created statements

![](/assets/images/2021-02-25-14-24-34.png)

Here Wikidata tells us that if we add an InChiKey we will need to also add an InChI. Logical, but good to have a reminder !

Let's go ahead and add this InChI string

Likewise the addition of an isomeric SMILES string will require us to add a Canonical SMILES
Mind that you could have to copy and paste the SMILES string from Pubchem to a plain text editor and then back to wikidata because of some formatting issues when copy pasting directly from Pubchem.

```
C[C@@H]1C2[C@]([C@H]3[C@H]4[C@]1(C5=CC(=C(Cl)Cl)[C@@H]([C@]5([C@@H]([C@@]6([C@H]4O6)COC(=O)C)OC(=O)C)O)OC(=O)C7=CC=CC=C7)OC(O3)(O2)C8=CC=CC=C8)(C(=C)C)O

CC1C2C(C3C4C1(C5=CC(=C(Cl)Cl)C(C5(C(C6(C4O6)COC(=O)C)OC(=O)C)O)OC(=O)C7=CC=CC=C7)OC(O2)(O3)C8=CC=CC=C8)(C(=C)C)O
```

### Adding the biological source information

Now let's add the found in taxon property

Just click on add a new statement and type in the first letters of the property you want to add 

![](/assets/images/2021-02-25-14-31-56.png)

Again type in the first letters of the taxa and if the organism is present it will autocomplete. Here it's Trigonostemon cherrieri.

(describe how to proceed if the organism is not present on wikidata)

![](/assets/images/2021-02-25-14-33-14.png)

Click publish to validate your action.

### Adding the reference documenting the structure-organism pair

Finally since we report documented structure-organisms pairs we need to add the reference of this newly created pair.
This happens just below the taxon we just added. Click on the 0 reference link and then on add reference

![](/assets/images/2021-02-25-14-35-33.png)

Here we use the stated in property (PXXXX)

![](/assets/images/2021-02-25-14-36-33.png)

Now type in the first letters or word of the scientific publication documenting the natural product occurence, autocompletion happens again.
Describe which steps to take if the reference is not existing 

![](/assets/images/2021-02-25-14-38-54.png)

Click the Publish action link above 

![](/assets/images/2021-02-25-14-39-48.png)

## Voila !

You have created your first documented structure-organism pairs and made a valuable contribution to the community.
You can add further statements (Molecular Formula, splash code linking to spectra etc etc)

This manually created entry is the following one https://www.wikidata.org/wiki/Q105674316

You can run a SPARQL query and check that everything went smoothly https://w.wiki/32WZ








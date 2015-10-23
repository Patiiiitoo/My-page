##EDAR-associated death domain: an aging-related gene in whales?
by Patricia Gayo de Linos [@Patiiiitoo](https://github.com/Patiiiitoo)

------------
It has been shown that some genes are age-related genes. This is the case of EDARADD or I think, so let's figure out!

I actually work with Balaenoptera musculus, best known as **Blue Whale** ![picture](http://www.oceanlight.com/stock-photo/blue-whale-mother-calf-aerial-photo-02304-782289.jpg),

but since there is no available sequence for this great mammal, I am going to work here with Balaenoptera acutorostrata, a related specie also known as **Minke whale** ![picture](http://marinebio.org/upload/balaenoptera-acutorostrata/6.jpg)

First, I did a NCBI search to see if there's any prior information about my query gene.

This is a screenshot of the NCBI

![picture](https://cloud.githubusercontent.com/assets/15118223/10680445/c8c8ae7c-78d4-11e5-9721-a2b5b2192fed.png)

And this is the link to the website if you want to know more about this gene:

<http://www.ncbi.nlm.nih.gov/gene/128178>

Then, I downloaded the EDARADD sequence from *Balaenoptera acutorostrata* in a FASTA format
![picture](https://cloud.githubusercontent.com/assets/15118223/10681775/cbfcadfc-78e1-11e5-9192-154fb2a74d64.PNG)

But before I run a BLAST I look for a human protein database so I can compare the whale sequence with the same gene in human proteins database, so I went to [UniProt Human Database](http://www.uniprot.org/uniprot/?query=*&fil=organism%3A%22Homo+sapiens+%28Human%29+%5B9606%5D%22) and downloaded the database.
To use it I need to descompress the file, so I did this in the command line with the next code:

```
gzip -d uniprot_all.fasta.gz
```

Then, I had to convert my FASTA file to a database, so I can make BLAST with my query sequence. To do that:


```	!makeblastdb \;
	-dbtype prot \; 
	-in uniprot_all.fasta \
	-out Human
```
And now I've got a new database created:
![picture](https://cloud.githubusercontent.com/assets/15118223/10682025/2039d950-78e5-11e5-8e37-91969fd6af47.PNG)

Then, I did BLAST using this code:

```!blastx \
-outfmt 7 \
-max_target_seqs 1 \
-evalue 1E-20 \
-query edaradd.fasta \
-db ../../big-data/blast/db/Human \
```

And I get only **_ONE match!_**

![picture](https://cloud.githubusercontent.com/assets/15118223/10682191/2dc77f76-78e7-11e5-8f2f-96e0db39f776.PNG)

Finally, I want to leave you here some information about the EDARADD gene and what it does in the human body:
>This gene was identified by its association with ectodermal dysplasia, a genetic disorder characterized by defective development of hair, teeth, and eccrine sweat glands.
>The protein encoded by this gene is a death domain-containing protein, and is found to interact with EDAR, a death domain receptor known to be required for the development of hair, teeth and other ectodermal derivatives. 
>This protein and EDAR are coexpressed in epithelial cells during the formation of hair follicles and teeth. Through its interaction with EDAR, this protein acts as an adaptor, and links the receptor to downstream signaling pathways *[RefSeq, Jul 2008]*

I also want to leave here a video from the National Foundation for Ectodermal Dysplasia, so you can understand a little more about this disease, if you don`t know already! :)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=REvzn1Uaq5s" target="_blank"><img src="http://img.youtube.com/vi/REvzn1Uaq5s/0.jpg" 
alt="Ectodermal Dysplasia" width="240" height="180" border="10" /></a>


So here it is!
Now I know that the EDARADD gene is conserved in a high level in mammals, and with importante effect in the development of disease so I think it's possible that it has an effect in marine mammals too.

Thanks! 

Tutorial
========

A quick tutorial to use CodAn.
The file ```transcripts.fa``` has 500 full transcript sequences from Danio rerio to test CodAn.
Donwload the ["VERT_full.zip"](https://github.com/pedronachtigall/CodAn/blob/master/models/VERT_full.zip) and ["VERT_partial.zip"](https://github.com/pedronachtigall/CodAn/blob/master/models/VERT_partial.zip) models avilable at the folder ["CodAn/models/"](https://github.com/pedronachtigall/CodAn/tree/master/models).

Running the Full model
======================

Decompress the model "VERT_full.zip":
```
unzip VERT_full.zip
```

Then, run CodAn:
```
codan.py -t transcripts.fa -m VERT_full
```

The output files will be available at the "CodAn_output" folder. If you want to specify the name of the output folder use the option ```-o output_folder```. CodAn uses only one thread by default ```-c 1```, but the user can specify the use of more threads by using the option ```-c int``` to accelerate the process.

Running the Partial model
=========================

Decompress the model "VERT_partial.zip":
```
unzip VERT_full.zip
```

Then, run CodAn:
```
codan.py -t transcripts.fa -m VERT_partial -o CodAn_partial_test
```

Running the BLAST search
========================
To run the BLAST search in the coding sequences predicted jut use the option ```-b``` and indicate the path to a protein blast database pre-designed or generated with the ```makeblastdb``` function from NCBI-BLAST.
```
makeblastdb -dbtype prot -in protein_sequences.fa -out blastDB
```

Then run CodAn with the following options:
```
codan.py -t transcripts.fa -m VERT_full -o CodAn_test_blast -b blastDB
```
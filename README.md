# Gene function annotation
Gene function annotation process code

## Data processing

### 1.InterPro annotation(GO, Pfam)

    interproscan.sh --applications ProDom,PRINTS,Pfam,SMART,PANTHER,ProSiteProfiles --disable-precalc --seqtype p --formats TSV --cpu 8 --goterms --pathways --input pep.fa --output-file-base InterPro_annotation/

### 2.KEGG annotation

    exec_annotation -f mapper -o KEGG_annotation/ pep.fa -p kofamscan/db/profiles/ -k kofamscan/db/ko_list --cpu 8

### 3.kog annotation

    diamond blastp --evalue 1e-05 --db /database/kog.fasta --query pep.fa --threads 6 --outfmt 6 --out KOG_annotation/KOG.blastp.out.m6

### 4.Swiss-Prot annotation

    diamond blastp --evalue 1e-05 --db /database/uniprot_sprot_animal.fa --query pep.fa --threads 8 --outfmt 6 'qseqid' 'sseqid' 'pident' 'length' 'mismatch' 'gapopen' 'qstart' 'qend' 'sstart' 'send' 'evalue' 'bitscore' 'stitle' --out Swiss-Prot_annotation/Swiss-Prot.blastp.out.m6



